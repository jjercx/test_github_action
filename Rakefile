require 'rake'

task :make_commit do
  require 'git'
  git = Git.open('.')

  require 'time'
  current_hour = Time.now.strftime("%H")
  File.write('current_hour.txt', current_hour)

  unless git.status.changed.find { |file, _| file == 'current_hour.txt' }
    puts 'No changes in current_hour.txt'
    exit(0)
  end

  puts 'Configuring git...'
  git.config('user.email', 'jjramirez@pucp.pe')
  git.config('user.name', 'Bot')

  puts 'Commiting changes...'
  git.add('current_hour.txt')
  git.commit('auto-commit')
  git.push('origin', 'HEAD')

  puts 'Changes commited'
end
