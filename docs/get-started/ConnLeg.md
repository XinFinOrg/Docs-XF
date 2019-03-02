# **ISO20022 Data Set APIs**

Captures data from ERP, SWIFT, Core Banking and wraps it under a ISO20022 data set. In the XDC Protocol, we add the transaction hash from private network or it's corresponding hash on the public network and append it to the Supplimentary data field in the ISO20022 data set.


[Reference Codebase](https://github.com/fairxio/finance-messaging)

# **ERP Connectors**

Connects and extracts data from SAP ERP system for applications such as inFactor.io or TradeFinex.org. 

This data can then be sent between private nodes using XDC Protocol Private(ISO20022)


[Reference Connector](https://github.com/SAP/node-rfc
Reference)

[Open Source ERP](https://github.com/frappe/erpnext)

# **Core Banking Connectors**

Captures data from banking systems such as accounts, balances, transactions. This data can be relayed on the XinFin Public Network or a private network.


[Reference Codebase](https://github.com/OpenBankProject)

# **SWIFT System Connectors**

Using SWIFT Network as rails by parsing the MT103 messages


[Reference Codebase](https://github.com/danielquinn/mt103)