# InDesignBookApply
Javascript code used for applying actions to all Documents (.indd) within a Book (.indb).

```javascript
main();

exit();

function main() {

     var myBook = app.activeBook, myDoc;

     var myDocs = myBook.bookContents.everyItem().getElements();

     for (var i=0; i< myDocs.length; i++) {

          /* Skip every 7th book (7, 14, 21, ...)
          if ((i + 1) % 7 == 0) {
               continue;	
          }
          */
          myDoc = app.open(File(myDocs[i].fullName));

           var myDoc = app.activeDocument;
           //Things that will apply to every book

           /* Paste in place
           //Choose layer
           myDoc.activeLayer = "SC";
           //Choose page
           myDoc.layoutWindows[0].activePage = app.activeDocument.pages[6];
           app.pasteInPlace();
           */

           /* Delete layer
           myDoc.layers.itemByName('watermark').remove();
           */

           /* Page orientation
           myDoc.documentPreferences.pageOrientation = 1751738216;
           */

           /* Bleed
           myDoc.documentPreferences.properties =
           {
               documentBleedUniformSize : true ,
               //Choose bleed size
               documentBleedTopOffset : "3 mm"
           };
           */

           /* Page add at end
           myDoc.documentPreferences.allowPageShuffle = true;

           var currentSpread = myDoc.spreads[1]

           currentSpread.allowPageShuffle = false;

           myDoc.pages.add(LocationOptions.AT_END);
           */

           /* Apply master page
           myDoc.pages[13].appliedMaster = myDoc.masterSpreads.item('C-Master');
           */

          //Close and save
          myDoc.close(SaveOptions.YES);

     }
     

}
```
