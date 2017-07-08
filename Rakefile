require 'rake'

# Loosely based on https://github.com/rkh/test-project-matrix-1
# Provide two tasks to generate webhook notifications
# for passing and failing builds

task :test_fail do
  (1..10).each do |n|
    sleep(1)
    puts "Building (#{n}/10)..."
    $stdout.flush
  end

  puts "Failing..."
  exit 1
end

task :test_pass do
  (1..10).each do |n|
    sleep(1)
    puts "Building (#{n}/10)..."
    $stdout.flush
  end

  puts "Passing..."
  exit 0
end

task :default => :test_pass