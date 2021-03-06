stream-ruby
=========

.. image:: https://circleci.com/gh/tbarbugli/stream-ruby.png?circle-token=48e057f56404d834093a73d6b783a94b5f6d6270
   :target: https://circleci.com/gh/tbarbugli/stream-ruby/tree/master


stream-ruby is a Ruby client for `Stream <https://getstream.io/>`_.

.. code-block:: ruby

    # Instantiate a new client
    require 'stream'
    client = Stream::Client.new('YOUR_API_KEY', 'API_KEY_SECRET')

    # Instantiate a feed object
    user_feed_1 = client.feed('user:1')

    # Get activities from 5 to 10 (slow pagination)
    result = user_feed_1.get(:limit=>5, :offset=>5)
    # (Recommended & faster) Filter on an id less than 112334
    result = user_feed_1.get(:limit=>5, :id_lt=>112334)
    
    # Create a new activity
    activity_data = {:actor => 1, :verb => 'tweet', :object => 1}
    activity_response = user_feed_1.add_activity(activity_data)

    # Remove an activity by its id
    user_feed_1.remove('12345678910')
    
    # Follow another feed
    user_feed_1.follow('flat:42')

    # Stop following another feed
    user_feed_1.unfollow('flat:42')
    
    
Docs are available on `GetStream.io`_.

.. _GetStream.io: http://getstream.io/docs/


Installation
------------

.. code-block:: bash

    gem "stream-ruby"

