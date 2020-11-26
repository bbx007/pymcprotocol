# pymcprotocol
MC Protocol(MELSEC Communication Protocol) implementation by Python

## Installation 
```console 
pip install pymcprotocol
```

## Protocol type
Now, pymcprotocol supports only mcprotocol 3E type.
In the future, support 4E type. (And if possible, 1C~4C type too...)

## How to use mc protocol
### 1. Set up PLC
First, you need to set upopen your PLC port to communicate by mcprotocol in Gxworks2 or Gxworks3.  
- Open port you want to communicate.  
- Select "Communication Data Code". If you select ascii type, you also need to set "ascii" in setaccessopt method. (default is "bainary")
- If you would like to write in to PLC, you also have to check __Enable online change__

### 2. Connect by Python
```python
import pymcprotocol

#If you use Q series PLC
pymc3e = pymcprotocol.Type3E()
#if you use L series PLC,
pymc3e = pymcprotocol.Type3E(plctype="L")
#if you use iQ series PLC,
pymc3e = pymcprotocol.Type3E(plctype="iQ")

#If you use ascii byte communication, (Default is "binary")
pymc3e.setaccessopt(commtype="ascii")
pymc3e.connect("192.168.1.2", 1025)

3. Send command
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: python
   #read from D100 to D110
   pymc3e.batchread_wordunits(headdevice="D100", size=10)

   #read from X10 to X20
   pymc3e.batchread_bitunits(headdevice="X10", size=10)
```

### 3. Communicate
```python
#read from D100 to D110
pymc3e.batchread_wordunits(headdevice="D100", size=10)

#read from X10 to X20
pymc3e.batchread_bitunits(headdevice="X10", size=10)

pymc3e.close()
```

### API Reference
API reference is depoloyed on here.  
https://pymcprotocol.netlify.app/