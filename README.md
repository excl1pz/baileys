# WhatsApp Baileys

<p align="center">
  <img src="https://github.com/excl1pz/Screaper/blob/main/exclipzpict.png" alt="Thumbnail" />
</p>

# @exclipz/baileys

<p>
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" />
  <img src="https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" />
  <img src="https://img.shields.io/badge/WebSocket-010101?style=for-the-badge&logo=socketdotio&logoColor=white" />
  <img src="https://img.shields.io/badge/Open%20Source-FF4500?style=for-the-badge&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/license-MIT-blue?style=for-the-badge" />
</p>
### Main Features and Advantages

- Supports automatic and custom pairing processes
- Fixes previous pairing issues that often caused failures or disconnections
- Supports interactive messages, action buttons, and dynamic menus
- Efficient automatic session management for reliable operation
- Compatible with the latest multi-device features from WhatsApp
- Lightweight, stable, and easy to integrate into various systems
- Suitable for developing bots, automation, and complete communication solutions
- Comprehensive documentation and example codes to facilitate development

---

## Getting Started

Begin by installing the library via your preferred package manager, then follow the provided configuration guide. You can also utilize the ready-made example codes to understand how the features work. Use session storage and interactive messaging features to build complete, stable solutions tailored to your business or project needs.

---

## SendMessage Documentation

### Album Message (Multiple Images)
Send multiple images in a single album message:

```javascript
await sock.sendMessage(jid, { 
  albumMessage: [
    { image: cihuy, caption: "Foto pertama" },
    { image: { url: "URL IMAGE" }, caption: "Foto kedua" }
    ] 
}, { quoted: m });
```

### Event Message
Create and send WhatsApp event invitations:

```javascript
await sock.sendMessage(jid, { 
  eventMessage: { 
    isCanceled: false, 
    name: "Hello World", 
    description: "Riyan Official Store Digital", 
    location: { 
      degreesLatitude: 0, 
      degreesLongitude: 0, 
      name: "Riyan Official" 
    },
    joinLink: "https://call.whatsapp.com/video/ShinVoc", 
    startTime: "1763019000", 
    endTime: "1763026200", 
    extraGuestsAllowed: false 
    } 
}, { quoted: m });
```

### Poll Result Message
Display poll results with vote counts:

```javascript
await sock.sendMessage(jid, {
  pollResultMessage: { 
    name: "Hello World", 
    pollVotes: [
      {
        optionName: "TEST 1",
        optionVoteCount: "112233"
      },
      {
        optionName: "TEST 2",
        optionVoteCount: "1"
      }
    ]
  } 
}, { quoted: m });
```

### Simple Interactive Message
Send basic interactive messages with copy button functionality:

```javascript
await sock.sendMessage(jid, {
  interactiveMessage: {
    header: "Hello World",
    title: "Hello World",
    footer: "telegram: @ShinVoc",
    buttons: [
      {
        name: "cta_copy",
        buttonParamsJson: JSON.stringify({
          display_text: "copy code",
          id: "123456789",              
          copy_code: "ABC123XYZ"
        })
      }
    ]
  }
}, { quoted: m });
```

### Interactive Message with Native Flow
Send interactive messages with buttons, copy actions, and native flow features:

```javascript
await sock.sendMessage(jid, {    
  interactiveMessage: {      
    header: "Hello World",
    title: "Hello World",      
    footer: "telegram: @ShinVoc",      
    image: { url: "https://example.com/image.jpg" },
    nativeFlowMessage: {        
      messageParamsJson: JSON.stringify({          
        limited_time_offer: {            
          text: "idk hummmm?",            
          url: "https://t.me/ShinVoc"
          copy_code: "ShinVoc",            
          expiration_time: Date.now() * 999          
        },          
        bottom_sheet: {            
          in_thread_buttons_limit: 2,            
          divider_indices: [1, 2, 3, 4, 5, 999],            
          list_title: "Riyan Native",            
          button_title: "Riyan Native"          
        },
        tap_target_configuration: {            
          title: " X ",            
          description: "bomboclard",            
          canonical_url: "https://t.me/ShinVoc",            
          domain: "shop.example.com",            
          button_index: 0          
        }        
      }),        
      buttons: [          
        {            
          name: "single_select",          buttonParamsJson: JSON.stringify({
            has_multiple_buttons: true
          })          
        },          
        {            
          name: "call_permission_request",
          buttonParamsJson: JSON.stringify({
            has_multiple_buttons: true            
          })          
        },          
        {            
          name: "single_select",            
          buttonParamsJson: JSON.stringify({
            title: "Hello World",              
            sections: [
              {                  
                title: "title",                  
                highlight_label: "label",
                rows: [                    
                  {                      
                    title: "@ShinVoc",
                    description: "love you",
                    id: "row_2"
                  }                  
                ]                
              }              
            ],              
            has_multiple_buttons: true            
          })          
        },          
        {            
          name: "cta_copy",            
          buttonParamsJson: JSON.stringify({
            display_text: "copy code",              
            id: "123456789",
            copy_code: "ABC123XYZ"
          })          
        }        
      ]      
    }    
  }  
}, { quoted: m });
```

### Interactive Message with Thumbnail
Send interactive messages with thumbnail image and copy button:

```javascript
await sock.sendMessage(jid, {
  interactiveMessage: {
    header: "Hello World",
    title: "Hello World",
    footer: "telegram: @ShinVoc",
    image: { url: "https://example.com/image.jpg" },
    buttons: [
      {
        name: "cta_copy",
        buttonParamsJson: JSON.stringify({
          display_text: "copy code",
          id: "123456789",
          copy_code: "ABC123XYZ"
        })
      }
    ]
  }
}, { quoted: m });
```

### Product Message
Send product catalog messages with buttons and merchant information:

```javascript
await sock.sendMessage(jid, {
  productMessage: {
    title: "Produk Contoh",
    description: "Ini adalah deskripsi produk",
    thumbnail: { url: "https://example.com/image.jpg" },
    productId: "PROD001",
    retailerId: "RETAIL001",
    url: "https://example.com/product",
    body: "Detail produk",
    footer: "Harga spesial",
    priceAmount1000: 50000,
    currencyCode: "USD",
    buttons: [
      {
        name: "cta_url",
        buttonParamsJson: JSON.stringify({
          display_text: "Beli Sekarang",
          url: "https://example.com/buy"
        })
      }
    ]
  }
}, { quoted: m });
```

### Interactive Message with Document Buffer
Send interactive messages with document from buffer (file system) - **Note: Documents only support buffer**:

```javascript
await sock.sendMessage(jid, {
  interactiveMessage: {
    header: "Hello World",
    title: "Hello World",
    footer: "telegram: @ShinVoc",
    document: fs.readFileSync("./package.json"),
    mimetype: "application/pdf",
    fileName: "ShinVoc.pdf",
    jpegThumbnail: fs.readFileSync("./document.jpeg"),
    contextInfo: {
      mentionedJid: [jid],
      forwardingScore: 777,
      isForwarded: false
    },
    externalAdReply: {
      title: "shenń Bot",
      body: "anu team",
      mediaType: 3,
      thumbnailUrl: "https://example.com/image.jpg",
      mediaUrl: " X ",
      sourceUrl: "https://t.me/ShinVoc",
      showAdAttribution: true,
      renderLargerThumbnail: false         
    },
    buttons: [
      {
        name: "cta_url",
        buttonParamsJson: JSON.stringify({
          display_text: "Telegram",
          url: "https://t.me/ShinVoc",
          merchant_url: "https://t.me/ShinVoc"
        })
      }
    ]
  }
}, { quoted: m });
```

### Interactive Message with Document Buffer (Simple)
Send interactive messages with document from buffer (file system) without contextInfo and externalAdReply - **Note: Documents only support buffer**:

```javascript
await sock.sendMessage(jid, {
  interactiveMessage: {
    header: "Hello World",
    title: "Hello World",
    footer: "telegram: @ShinVoc",
    document: fs.readFileSync("./package.json"),
    mimetype: "application/pdf",
    fileName: "ShinVoc.pdf",
    jpegThumbnail: fs.readFileSync("./document.jpeg"),
    buttons: [
      {
        name: "cta_url",
        buttonParamsJson: JSON.stringify({
          display_text: "Telegram",
          url: "https://t.me/ShinVoc",
          merchant_url: "https://t.me/ShinVoc"
        })
      }
    ]
  }
}, { quoted: m });
```

### Request Payment Message
Send payment request messages with custom background and sticker:

```javascript
let quotedType = m.quoted?.mtype || '';
let quotedContent = JSON.stringify({ [quotedType]: m.quoted }, null, 2);

await sock.sendMessage(jid, {
  requestPaymentMessage: {
    currency: "IDR",
    amount: 10000000,
    from: m.sender,
    sticker: JSON.parse(quotedContent),
    background: {
      id: "100",
      fileLength: "0",
      width: 1000,
      height: 1000,
      mimetype: "image/webp",
      placeholderArgb: 0xFF00FFFF,
      textArgb: 0xFFFFFFFF,     
      subtextArgb: 0xFFAA00FF   
    }
  }
}, { quoted: m });
```

---

## Why Choose WhatsApp Baileys?

Because this library offers high stability, full features, and an actively improved pairing process. It is ideal for developers aiming to create professional and secure WhatsApp automation solutions. Support for the latest WhatsApp features ensures compatibility with platform updates.

---

### Technical Notes

- Supports custom pairing codes that are stable and secure
- Fixes previous issues related to pairing and authentication
- Features interactive messages and action buttons for dynamic menu creation
- Automatic and efficient session management for long-term stability
- Compatible with the latest multi-device features from WhatsApp
- Easy to integrate and customize based on your needs
- Perfect for developing bots, customer service automation, and other communication applications

---

For complete documentation, installation guides, and implementation examples, please visit the official repository and community forums. We continually update and improve this library to meet the needs of developers and users of modern WhatsApp automation solutions.

**Thank you for choosing WhatsApp Baileys as your WhatsApp automation solution!**
