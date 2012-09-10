# Dependencies
require 'csv'

#Class Definition
class EventManager
  def initialize
	puts "EventManager Initialized."
	filename = "event_attendees.csv"
	@file = CSV.open(filename, {:headers => true, :header_converters => :symbol})
  end

  def print_names
	@file.each do |line|
	  #puts line.inspect
	  puts line[:first_name] +" "+ line[:last_name]
	end
  end

  def print_numbers
	@file.each do |line|
	  number = clean_number(line[:homephone])
	  puts number
	end
  end

  def clean_number(number)
	  number.delete!("^0-9")
	  if number.length == 10
		#Do Nothing
	  elsif number.length == 11
		if number.start_with?("1")
		  number = number[1..-1]
		else
		  number = "0"
		end
	  else
		number = "0"
	  end
	number
  end

  def print_zipcodes
	@file.each do |line|
	  zipcode = clean_zipcode(line[:zipcode])
	  puts zipcode
	end
  end

  def clean_zipcode(original)
	zipcode = original.to_s
	if zipcode.length < 5 #doesn't deal with nil values
	  zipcode = "%05d" % zipcode
	end
	zipcode
  end
end

#Script
manager = EventManager.new
#manager.print_names
#manager.print_numbers
manager.print_zipcodes
