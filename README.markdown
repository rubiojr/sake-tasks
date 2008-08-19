## Installation

First, clone the sake-tasks repo:

	git clone git://github.com/drnic/sake-tasks.git

Or replace 'drnic' with your github username if you have forked the sake-tasks repo.

Then install the sake tasks (this step is repeatable, even if one or more tasks are already exist; that is, any pre-existing tasks with the same name will be overridden)

	rake install

To see your list of resulting tasks:

	sake -T

## What are Sake tasks/recipes?

It's the marvelous Sake, system-wide Rake.  
http://errtheblog.com/posts/60-sake-bomb

## Adding new recipes/tasks

The installer rake task `rake install` works by assuming that each `.sake` file contains one sake task. This allows it to uninstall the task from sake first, and then re-install it (sake barfs if you attempt to reinstall an existing task).

So, to create a task `foo:bar:baz`, you'll need to add a folder `foo/bar` and create a file `baz.sake` inside it. Within that file you would then specify your task using `namespace` and `task` method calls:

	namespace 'foo' do
	  namespace 'bar' do
	    desc "This task ..."
	    task :baz do

	    end
	  end
	end

### TextMate users

The latest [Ruby.tmbundle](http://github.com/drnic/ruby-tmbundle) on github includes a `task` command that generates the above namespace/task snippet based on the path + file name. That is, inside the `foo/bar/baz.sake` file, make sure your grammar is 'Ruby' or 'Ruby on Rails' and then type "task" and press TAB. The above snippet will be generated ready for you to specify your task.

## Authors

* Luke Melia - many git + mysql + ssh tasks
* Dr Nic Williams - repeatable installer rake task
