#Migrations

##Creating
```ruby
 def change
   create_table :tasks do |t|
     t.references :user, foreign_key: true (, index:true)
     t.string :city, index: { unique: true}
     t.references :offer
   end
    
   add_foreign_key :tasks, :offers, on_delete: :cascade
  
  end
    
```

##Updating
```
def change
  add_column :tasks, :category, :integer
  add_index :tasks, :category
end
```

```
change_table(:suppliers) do |t|
  t.column :name, :string, limit: 60
  # Other column alterations here
end
```