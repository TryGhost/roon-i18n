desc 'Give a report of incomplete translations'
task :incomplete do
  require 'yaml'

  # Open English to get all of the keys
  en_keys = YAML.load(File.open('web/en.yml'))['en']['viewer'].keys

  # Loop through the rest of the languages and print a report
  Dir.foreach('web') do |file|
    # Skip . and ..
    next if file[0] == '.'

    # Get the language from the file name
    language = file.sub('.yml', '')

    # Load the keys
    keys = YAML.load(File.open("web/#{file}"))[language]['viewer'].keys

    # Find missing keys
    missing_keys = en_keys - keys

    if missing_keys.length > 0
      puts "#{language}:"
      missing_keys.each do |key|
        puts "  #{key}"
      end
      puts
    end
  end
end
