ModelMapper
===========

A ORM inspired by Ruby's DataMapper and ActiveRecord

Getting started (jruby)
===========

require 'java'
require 'package/modelmapper.jar'

include_class Java::modelmapper.provider.mysql.MySQLModelFactory
include_class Java::modelmapper.Finder 

require 'package/model.jar'  
include_class Java::mymodel.Student


f = MySQLModelFactory.new("jdbc:mysql://localhost/mapper", "root", "")     

student_finder = Finder.new(Student.java_class, f)    

find_age = student_finder.where("age", [22, 28, 20].to_java)

s = find_age.first();
s.to_string

s.department

s.corporations[0].to_string
s.corporations[0].ceo.to_string
s.corporations[0].ceo.age 

webservice = s.web_service
webservice.to_string

webservice.accounts[0].to_string
webservice.accounts[1].to_string
