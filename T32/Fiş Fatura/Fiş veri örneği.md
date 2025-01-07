const generateReceiptHTML = (receiptData) => {
  return `
    <div style="font-family: Arial, sans-serif;">
      <h2 style="text-align: center;">T32 GROCERY</h2>
      <p style="text-align: center;">Sakarya Univ. Computer Science Dept. 143/2</p>
      <p style="text-align: center;">Sakarya</p>
      <div style="margin-top: 10px; display: flex; justify-content: space-between;">
        <span>Date: ${receiptData.date}</span>
        <span>Time: ${receiptData.time}</span>
      </div>
      <div style="display: flex; justify-content: space-between;">
        <span>Sale No: ${receiptData.saleNo}</span>
        <span>Cashier: ${receiptData.cashier}</span>
      </div>
      <hr style="border: 1px dashed; margin-top: 10px; margin-bottom: 10px;" />
      ${receiptData.items.map(item => `
        <div>
          <p>${item.code} (${item.quantity} Adet X ${item.unitPrice.toFixed(2)})</p>
          <div style="display: flex; justify-content: space-between;">
            <span>${item.name}</span>
            <span>${item.totalPrice.toFixed(2)} ₺</span>
          </div>
        </div>
        <hr style="margin-top: 5px; margin-bottom: 5px;" />
      `).join('')}
      <hr style="border: 1px dashed; margin-top: 10px; margin-bottom: 10px;" />
      <div style="display: flex; justify-content: space-between;">
        <span>Total Received:</span>
        <span>${receiptData.totalReceived} ₺</span>
      </div>
      <div style="display: flex; justify-content: space-between;">
        <span>Total Taxes:</span>
        <span>${receiptData.totalTaxes} ₺</span>
      </div>
      <hr style="border: 1px dashed; margin-top: 10px; margin-bottom: 10px;" />
      <div style="display: flex; justify-content: space-between;">
        <span>Subtotal:</span>
        <span>${receiptData.subtotal} ₺</span>
      </div>
      <div style="display: flex; justify-content: space-between;">
        <span>Discount:</span>
        <span>${receiptData.discount} ₺</span>
      </div>
      <div style="display: flex; justify-content: space-between;">
        <span>Change Given:</span>
        <span>${receiptData.changeGiven} ₺</span>
      </div>
      <hr style="border: 1px dashed; margin-top: 10px; margin-bottom: 10px;" />
      <div style="display: flex; justify-content: space-between;">
        <span>Grand Total:</span>
        <span>${receiptData.grandTotal} ₺</span>
      </div>
    </div>
  `;
};



<div style="font-family: Arial, sans-serif;"> <h2 style="text-align: center;">T32 GROCERY</h2> <p style="text-align: center;">Sakarya Univ. Computer Science Dept. 143/2</p> <p style="text-align: center;">Sakarya</p> <div style="margin-top: 10px;"> <span style="float: left;">Date: ${receiptData.date}</span> <span style="float: right;">Time: ${receiptData.time}</span> <div style="clear: both;"></div> </div> <div> <span style="float: left;">Sale No: ${receiptData.saleNo}</span> <span style="float: right;">Cashier: ${receiptData.cashier}</span> <div style="clear: both;"></div> </div> <hr style="border: 1px dashed; margin-top: 10px; margin-bottom: 10px;" /> ${receiptData.items.map((item) => ` <div> <p>${item.code} (${item.quantity} Adet X ${item.unitPrice.toFixed(2)})</p> <div> <span style="float: left;">${item.name}</span> <span style="float: right;">${item.totalPrice.toFixed(2)} ₺</span> <div style="clear: both;"></div> </div> </div> <hr style="margin-top: 5px; margin-bottom: 5px;" /> `).join('')} <hr style="border: 1px dashed; margin-top: 10px; margin-bottom: 10px;" /> <div> <span style="float: left;">Total Received:</span> <span style="float: right;">${receiptData.totalReceived} ₺</span> <div style="clear: both;"></div> </div> <div> <span style="float: left;">Total Taxes:</span> <span style="float: right;">${receiptData.totalTaxes} ₺</span> <div style="clear: both;"></div> </div> <hr style="border: 1px dashed; margin-top: 10px; margin-bottom: 10px;" /> <div> <span style="float: left;">Subtotal:</span> <span style="float: right;">${receiptData.subtotal} ₺</span> <div style="clear: both;"></div> </div> <div> <span style="float: left;">Discount:</span> <span style="float: right;">${receiptData.discount} ₺</span> <div style="clear: both;"></div> </div> <div> <span style="float: left;">Change Given:</span> <span style="float: right;">${receiptData.changeGiven} ₺</span> <div style="clear: both;"></div> </div> <hr style="border: 1px dashed; margin-top: 10px; margin-bottom: 10px;" /> <div> <span style="float: left;">Grand Total:</span> <span style="float: right;">${receiptData.grandTotal} ₺</span> <div style="clear: both;"></div> </div> </div>



<div style="font-family: Arial, sans-serif; padding:5px"> ${zReport ? '<p>Z Report</p>' : ''} <h2 style="text-align: center;">T32 GROCERY</h2> <p style="text-align: center;">Sakarya Univ. Computer Science Dept. 143/2</p> <p style="text-align: center;">Sakarya</p> <div style="margin-top: 10px;"> <span style="float: left;">Date: ${receiptData.date}</span> <span style="float: right;">Time: ${receiptData.time}</span> <div style="clear: both;"></div> </div> <div> <span style="float: left;">Sale No: ${receiptData.saleNo}</span> <span style="float: right;">Cashier: ${receiptData.cashier}</span> <div style="clear: both;"></div> </div> ${!zReport ? ` <hr style="border: 1px dashed; margin-top: 10px; margin-bottom: 10px;" /> ${receiptData.items.map((item) => ` <div> <p>${item.code} (${item.quantity} Adet X ${item.unitPrice.toFixed(2)})</p> <div> <span style="float: left;">${item.name}</span> <span style="float: right;">${item.totalPrice.toFixed(2)} ₺</span> <div style="clear: both;"></div> </div> <hr style="margin-top: 5px; margin-bottom: 5px;" /> </div> `).join('')} ` : ''} <hr style="border: 1px dashed; margin-top: 10px; margin-bottom: 10px;" /> <div> <span style="float: left;">Total Received:</span> <span style="float: right;">${receiptData.totalReceived} ₺</span> <div style="clear: both;"></div> </div> <div> <span style="float: left;">Total Taxes:</span> <span style="float: right;">${receiptData.totalTaxes} ₺</span> <div style="clear: both;"></div> </div> <hr style="border: 1px dashed; margin-top: 10px; margin-bottom: 10px;" /> ${!zReport ? ` <div> <span style="float: left;">Subtotal:</span> <span style="float: right;">${receiptData.subtotal} ₺</span> <div style="clear: both;"></div> </div> ` : ''} <div> <span style="float: left;">Discount:</span> <span style="float: right;">${receiptData.discount} ₺</span> <div style="clear: both;"></div> </div> ${!zReport ? ` <div> <span style="float: left;">Change Given:</span> <span style="float: right;">${receiptData.changeGiven} ₺</span> <div style="clear: both;"></div> </div> ` : ''} <hr style="border: 1px dashed; margin-top: 10px; margin-bottom: 10px;" /> ${zReport ? ` <div> <span style="float: left;">Card Payment Total:</span> <span style="float: right;">${receiptData.cardPayment} ₺</span> <div style="clear: both;"></div> </div> <div> <span style="float: left;">Cash Payment Total:</span> <span style="float: right;">${receiptData.cashPayment} ₺</span> <div style="clear: both;"></div> </div> ` : ''} ${!zReport ? ` <div> <span style="float: left;">Grand Total:</span> <span style="float: right;">${receiptData.grandTotal} ₺</span> <div style="clear: both;"></div> </div> ${receiptData.mail ? ` <hr style="border: 1px dashed; margin-top: 10px; margin-bottom: 10px;" /> <div> <span style="float: left;">Mail Address:</span> <span style="float: right;">${receiptData.mail}</span> <div style="clear: both;"></div> </div> ` : ''} ` : ''} </div>