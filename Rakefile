desc "Install sake tasks, uninstalling any pre-existing tasks first"
task :install do
  task_files = Dir['**/*.sake']
  task_files.sort.map do |task_file|
    sake_task = task_file.gsub('/', ':').gsub('.sake','')
    puts `sake -u #{sake_task}`
    puts `sake -i #{task_file}`
  end
end

desc "Run latest source of task"
task :testrun do
  task_names = ARGV.grep(/(.+:)+/)
  
  task_names.each do |task_name|
    sake_file = task_name.gsub(':','/') + '.sake'
    import(sake_file) if File.exists?(sake_file)

    Rake.application.load_imports
    (task_names << Rake::Task[task_name].prerequisites).flatten!
  end
end

task :default => :install