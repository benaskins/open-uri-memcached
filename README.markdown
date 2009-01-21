OpenURI with Memcached caching
--

Carelessly make heavy OpenURI calls as many times as you like with local
memcached picking up the slack and stopping people from sending you hate mail.

Require the library using 
  require 'openuri_memcached'
  
To get started run your memcached server
  $ memcached -d 
The default address that this gem will terminate against is localhost:11211, you can change this using
  OpenURI::Cache.host = ['10.1.1.10:11211', '10.1.1.11:11211']

The cache defaults to 15 minutes, however this can be changed using:
  OpenURI::Cache.expiry = 60 * 10 # Ten long minutes
  
Execution
Use exactly the same as you would openuri, only.. enable it.

  require 'openuri_memcached'
  OpenURI::Cache.enable!
  open("http://germanforblack.com").read # Slow as a wet week
  
Quit your app (leave memcached running) and run the same example, it 
should now happen in less then ... some time that is really fast.

Questions and comments can be directed to ben at germanforblack.com

Requirements: 
	» Ruby 1.8.6
	» Memcached 
	» memcache - Refer to blog.evanweaver.com/files/doc/fauna/memcached/files/README.html for installation notes
	 For the gem, do this `sudo env ARCHFLAGS="-arch i386" gem install memcached --no-rdoc --no-ri -- --with-opt-dir=/opt/local`
	