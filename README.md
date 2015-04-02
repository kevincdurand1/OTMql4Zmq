# OTMql4Zmq
## Open Trading Metaquotes4 ZeroMq Bridge

MQL4ZMQ - MQL4 bindings for ZeroMQ  

Based in work by 2012 Austen Conrad:
https:///github.com/AustenConrad/mql4zmq

From AustenConrad/mql4zmq/mql4zmq.c:

The reason for all of this is that MetaTrader is a visual basic
application and therefore is written using the STDCALL calling
convention while ZeroMQ dll EXPORT defaults to the standard C calling
convention (CDECL). If not changed, a call to libzmq.dll from
MetaTrader will result in the trading terminal crashing.

Therefore, this file generates mql4zmq.dll which wraps each call the
zmq.h exports when compiled as libzmq.dll (i.e. each function that has
ZMQ_EXPORT preceeding it) as a STDCALL instead (i.e. __stdcall via
WINAPI definition).

Additionally, MetaTrader4 has limitations on datatypes and data
structures that we attempt to resolve by having the wrapping funtion
inputs being of a type and in a manner that will jive with MQL4.

NAMING NOTE: To avoid naming collisions with the original zmq.h
definitions we renamed our exported functions with 'mql4' appended to
the beginning of the name.  In the mql4zmq.mqh we revert the names
back to the original to reduce confusion when writing experts.
