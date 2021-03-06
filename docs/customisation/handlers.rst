Handlers
========

Now we want to integrate the stream/function from the last example (:doc:`/customisation/streamfunction`) into the :class:`secsgem.gem.handler.GemHandler`.
You create a new class inherited from the GemHandler and update the function list of that class::

    class NewHandler(secsgem.GemHostHandler):
        def __init__(self, address, port, active, session_id, name, event_handler=None, custom_connection_handler=None):
            secsgem.GemHostHandler.__init__(self, address, port, active, session_id, name, event_handler, custom_connection_handler)

            self.secsStreamsFunctions[1].update({
                12: SecsS01F12_New,
            })

You can also add new methods and properties to the class if required.

This new class can be used with the :class:`secsgem.hsms.connectionmanager.HsmsConnectionManager` (see parameter connection_handler of :func:`secsgem.hsms.connectionmanager.HsmsConnectionManager.add_peer`)