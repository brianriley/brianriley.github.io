---
title: "UUID Fields in Phoenix"
---

[Phoenix](http://www.phoenixframework.org) is still a young framework. As such, you may encounter problems that no one else has or problems that are just slightly different than others. This is a story of the latter.

I have a model that I want to have a UUID as its `id`. After a little searching, I came across this [StackOverflow post](http://stackoverflow.com/questions/30004008/setting-up-phoenix-framework-and-ecto-to-use-uuids-how-to-insert-the-generated). It's great---worked for me the first time. Until I added other models.

The changes you make to `web.ex` in this solution force *all* models to have UUIDs as `id`s. It took me a while to realize that the solution to my specific problem was to move those edits to `web.ex` into my model, but when I did that I kept getting validation errors about my UUID not being an integer. After spending a bunch of time looking into source code and chatting on IRC, I realized that I was looking at an ordering problem: the definitions of the `id` field need to come before the `schema` block.

~~~ elixir
defmodule MyApp.MyModel
  use MyApp.Web, :model

  # The following needs to be before the schema declaration
  # to properly take effect
  @primary_key {:id, Ecto.UUID, read_after_writes: true}
  @foreign_key_type Ecto.UUID

  schema "my_models" do
    ...
  end
end
~~~


And there you have it. I also left out the `before_insert MyApp.UUID, :put_uuid, []` part, which just has the database generate the UUID for me, as it does integer `id`s.

As José says in the SO post, working with UUIDs is likely to be improved in the future. This is echoed somewhat in [Chris McCord's keynote](http://www.chrismccord.com/blog/2015/05/09/elixirconfeu-keynote-phoenix-takes-flight/) where he mentions that token auth for channels is a feature they're looking to add in the future. (I'm using UUIDs as tokens for auth in my application.)
