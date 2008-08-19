desc "Install sake tasks, uninstalling any pre-existing tasks first"
task :install do
  task_files = Dir['**/*.sake']
  task_files.sort.map do |task_file|
    sake_task = task_file.gsub('/', ':').gsub('.sake','')
    puts `sake -u #{sake_task}`
    puts `sake -i #{task_file}`
  end
end

task :default => :install