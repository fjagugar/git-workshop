# Git Workshop

This repository contains some exercises for practicing your git skills.
For performing these exercises, just clone the repo in your local environment and perform the changes proposed in the exercises.

# Exercise 1

  1. Create a branch *branch1* from master
  1. Create a new file called dog.rb with the following content:

~~~rb
class Dog
  def initialize(breed, name)
    # Instance variables
    @breed = breed
    @name = name
  end

  def bark
    puts 'Ruff! Ruff!'
  end

  def display
    puts "I am of #{@breed} breed and my name is #{@name}"
  end
end
~~~

  1. Create a new commit in this branch with the new file created. The title of the commit should be "Added dog.rb"
  1. Create a new branch called *branch2* from this branch.
  1. Create a new file called cat.rb with the following content:

~~~rb
class Cat
  def initialize(breed, name)
    # Instance variables
    @breed = breed
    @name = name
  end

  def meow
    puts 'Meow! Meow!'
  end

  def display
    puts "I am of #{@breed} breed and my name is #{@name}"
  end
end
~~~

  1. Create a new commit at *branch2* with the new file added. The title of the commit should be "Added cat.rb"
  1. From *branch2*, create a new branch called *branch3*
  1. Create a file called apple.js with the following content:

~~~js
function Apple (type) {
    this.type = type;
    this.color = "red";
    this.getInfo = function() {
        return this.color + ' ' + this.type + ' apple';
    };
}
~~~

  1. Create a commit at *branch3* with the new filled created. The title of the commit should be "Wrong commit name"
  1. Change the title of the previous commit to "Added apple.js"

## Result of Exercise 1

At the end of this exercise you should have something similar to this:

~~~sh
$ git log --graph --abbrev-commit --decorate --oneline --all
* a851c68 (HEAD, branch3) Added apple.js
* 04d56d4 (branch2) Added cat.rb
* 770459b (branch1) Added dog.rb
* 3bd165a (origin/master, origin/HEAD, master) Initial commit
~~~

# Exercise 2

  1. Change upstream of *branch2* to point *branch1*
  1. Change upstream of *branch3* to point *branch2*
  1. Move to *branch1* and edit dog.rb file. Add an attribute *color* to the class Dog.
  1. Create a commit in *branch1* with the modification performed in the dog.rb file. The title of the commit should be "Added color to dog class"
  1. Perform the necessary changes in the git history so *branch2* and *branch3* contains the following commits in the same order as listed here:

  ~~~
  $ git log branch2 --oneline
  f805d09 Added cat.rb
  82c81de Added color to dog class
  770459b Added dog.rb
  3bd165a Initial commit
  ~~~

  ~~~
  $ git log branch3 --oneline
  2bc1158 Added apple.js
  f805d09 Added cat.rb
  82c81de Added color to dog class
  770459b Added dog.rb
  3bd165a Initial commit
  ~~~


## Result of Exercise 2

At the end of this exercise you should have something similar to this:

~~~sh
$ git log --graph --abbrev-commit --decorate --oneline --all
* 2bc1158 (HEAD, branch3) Added apple.js
* f805d09 (branch2) Added cat.rb
* 82c81de (branch1) Added color to dog class
* 770459b Added dog.rb
* 3bd165a (origin/master, origin/HEAD, master) Initial commit
~~~

# Exercise 3

  1. Add the attribute color to the cat class and add this change as a new commit of branch2. The title of the commit should be 'Added color to cat'.
  1. Merge all the commits present at branch2 into branch1, so the log at branch1 looks similar to this:

~~~sh
$ git log --oneline
81d4166 Added cat.rb with color attribute
82c81de Added color to dog class
770459b Added dog.rb
3bd165a Initial commit
~~~

  1. Delete branch2
  1. Rebase branch1 onto branch3, so the log of branch3 is similar to this:

~~~sh
$ git log --oneline
fb64360 Added apple.js
81d4166 Added cat.rb with color attribute
82c81de Added color to dog class
770459b Added dog.rb
3bd165a Initial commit
~~~

## Result of Exercise 3

At the end of this exercise you should have something similar to this:

~~~sh
$ git log --graph --abbrev-commit --decorate --oneline --all
* fb64360 (HEAD, branch3) Added apple.js
* 81d4166 (branch1) Added cat.rb with color attribute
* 82c81de Added color to dog class
* 770459b Added dog.rb
* 3bd165a (origin/master, origin/HEAD, master) Initial commit
~~~

# Exercise 4

  1. Add a new commit to branch1, with a file lorem.txt with the following content:

~~~
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam ligula felis, laoreet sit amet egestas feugiat, auctor non purus. Nulla facilisi. Sed eu tempor massa, et vehicula urna. Maecenas ac quam non magna tempus rutrum. Maecenas in ullamcorper ex. Ut porttitor eget purus sit amet vestibulum. Integer mollis mauris sed nunc volutpat, vitae mattis tortor venenatis. Nunc eu risus quis arcu lobortis rhoncus. Ut imperdiet nisl nunc, ac porttitor ligula rhoncus eget. Pellentesque eu pulvinar magna. Vestibulum ac diam in velit venenatis dapibus. Morbi mollis ac elit a ullamcorper. In dapibus nisi ut auctor molestie. Nunc scelerisque, orci finibus commodo efficitur, magna est dapibus lectus, quis rhoncus turpis mi eget neque.

Suspendisse vel efficitur augue. Morbi sed posuere ante. Etiam vel nibh rhoncus, dignissim ante eu, luctus dolor. Sed fermentum venenatis sem, in lacinia libero vestibulum sit amet. In vestibulum efficitur dui id scelerisque. Morbi condimentum odio at libero tempor mattis. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Aenean mattis ipsum quis volutpat elementum.
~~~

The tile of the commit should be 'Added lorem'

  1. Now, move this commit to a new branch called branch4. This branch should have the same commits present in branch1 and the new "Added lorem" commit. Branch1 should not have this commit.


## Result of Exercise 4

At the end of this exercise you should have something similar to this:

~~~sh
$ git log branch1..branch4 --oneline
a592bab Added lorem
~~~


# Exercise 5

 1. Go to branch4. Let's edit cat.rb file. Perform some small modifications in it.
 1. Perform some small modifications to dog.rb file.
 1. Perform some small modifications to lorem.txt
 1. Save the changes performed at lorem.txt in this branch and move to branch1
 1. Go back to branch1 and add the changes performed in cat.rb as a new commit.
 1. Stash the changes pending in dog.rb for finishing them later on.
 1. Go back to branch4, and unstage the changes you saved for lorem.txt

# Exercise 6

  1. Continuing on branch4, check the differences between your current cat.rb file, and the version present at branch1.
  1. Without changing the branch, check the full content of the file cat.rb at the branch1.
  1. Commit your changes pending in lorem.txt file at branch4.
  1. Move to branch3, and check the full content of lorem.txt at branch4

# Last Exercise

Just remove all the branches created.
