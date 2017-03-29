<%= form_for(thought) do |f| %>
  <% if thought.errors.any? %>
    <div id="error_explanation">
      <h2><%= pluralize(thought.errors.count, "error") %> prohibited this thought from being saved:</h2>

      <ul>
      <% thought.errors.full_messages.each do |message| %>
        <li><%= message %></li>
      <% end %>
      </ul>
    </div>
  <% end %>

  <div class="field">
    <%= f.label :content %>
    <%= f.text_field :content %>
  </div>

  <div class="actions">
    <%= f.submit %>
  </div>
<% end %>


```
<form class="new_thought" id="new_thought" action="/thoughts" accept-charset="UTF-8" method="post"><input name="utf8" type="hidden" value="&#x2713;" />
  <div class="field">
    <label for="thought_content">Content</label>
    <input type="text" name="thought[content]" id="thought_content" />
  </div>

  <div class="actions">
    <input type="submit" name="commit" value="Create Thought" data-disable-with="Create Thought" />
  </div>
</form>
```

```
Started POST "/thoughts" for 127.0.0.1 at 2017-03-29 11:02:31 -0700
Processing by ThoughtsController#create as HTML
  Parameters: {"utf8"=>"✓", "thought"=>{"content"=>"no form tag"}, "commit"=>"Create Thought"}
Can't verify CSRF token authenticity.
Completed 422 Unprocessable Entity in 1ms (ActiveRecord: 0.0ms)
  
ActionController::InvalidAuthenticityToken (ActionController::InvalidAuthenticityToken):
```


  protect_from_forgery with: :null_session
  
  Started POST "/thoughts" for 127.0.0.1 at 2017-03-29 11:04:31 -0700
  Processing by ThoughtsController#create as HTML
    Parameters: {"utf8"=>"✓", "thought"=>{"content"=>"sdfasfsa"}, "commit"=>"Create Thought"}
  Can't verify CSRF token authenticity.
     (0.1ms)  begin transaction
    SQL (0.4ms)  INSERT INTO "thoughts" ("content", "created_at", "updated_at") VALUES (?, ?, ?)  [["content", "sdfasfsa"], ["created_at", 2017-03-29 18:04:31 UTC], ["updated_at", 2017-03-29 18:04:31 UTC]]
     (0.8ms)  commit transaction
  Redirected to http://localhost:3000/thoughts/3
  Completed 302 Found in 5ms (ActiveRecord: 1.3ms)
  
  
  :reset_session
  
  
  Started POST "/thoughts" for 127.0.0.1 at 2017-03-29 11:06:27 -0700
  Processing by ThoughtsController#create as HTML
    Parameters: {"utf8"=>"✓", "thought"=>{"content"=>"testing reset session"}, "commit"=>"Create Thought"}
  Can't verify CSRF token authenticity.
     (0.1ms)  begin transaction
    SQL (0.5ms)  INSERT INTO "thoughts" ("content", "created_at", "updated_at") VALUES (?, ?, ?)  [["content", "testing reset session"], ["created_at", 2017-03-29 18:06:27 UTC], ["updated_at", 2017-03-29 18:06:27 UTC]]
     (1.3ms)  commit transaction
  Redirected to http://localhost:3000/thoughts/4
  Completed 302 Found in 5ms (ActiveRecord: 1.9ms)
  
  
  
  curl -H "Content-Type: application/json" -X POST -d '{"thought"=>{"content"=>"testing reset session using curl"}, "commit"=>"Create Thought"}' http://localhost:3000/thoughts
  
  Started POST "/thoughts" for 127.0.0.1 at 2017-03-29 11:10:25 -0700
  Error occurred while parsing request parameters.
  Contents:

  {"thought"=>{"content"=>"testing reset session using curl"}, "commit"=>"Create Thought"}
  
  ActionDispatch::ParamsParser::ParseError (822: unexpected token at '{"thought"=>{"content"=>"testing reset session using curl"}, "commit"=>"Create Thought"}'):
  
  
  
  JSON Lint
  
  {
  	"thought": {
  		"content": "testing reset session using curl"
  	},
  	"commit": "Create Thought"
  }
  
    curl -H "Content-Type: application/json" -X POST -d '{"thought":{"content":"testing reset session using curl"}, "commit":"Create Thought"}' http://localhost:3000/thoughts
    
    $curl -H "Content-Type: application/json" -X POST -d '{"thought":{"content":"testing reset session using curl"}, "commit":"Create Thought"}' http://localhost:3000/thoughts
    <html><body>You are being <a href="http://localhost:3000/thoughts/5">redirected</a>.</body></html>
    
    
    Started POST "/thoughts" for 127.0.0.1 at 2017-03-29 11:15:07 -0700
    Processing by ThoughtsController#create as */*
      Parameters: {"thought"=>{"content"=>"testing reset session using curl"}, "commit"=>"Create Thought"}
    Can't verify CSRF token authenticity.
       (0.1ms)  begin transaction
      SQL (0.4ms)  INSERT INTO "thoughts" ("content", "created_at", "updated_at") VALUES (?, ?, ?)  [["content", "testing reset session using curl"], ["created_at", 2017-03-29 18:15:07 UTC], ["updated_at", 2017-03-29 18:15:07 UTC]]
       (1.0ms)  commit transaction
    Redirected to http://localhost:3000/thoughts/5
    Completed 302 Found in 4ms (ActiveRecord: 1.5ms)
    
    
   