# tictactoe
## Project Setup

npm install


## Run

npm run dev


## วิธีออกแบบ

### มีตัวแปร

*__player__* เก็บ ผู้เล่น 

*__num__* เก็บ ขนาดของboard

*__showhistory__* เก็บ booleanที่ใช้แสดงhistory

*__squares__* เก็บ รูปแบบของช่อง4เหลี่ยม

*__history__* เก็บ arrayของhistoryทั้งหมด

*__historywinplayer__* เก็บ ผู้เล่นที่ชนะในhistory

*__historywinindex__* เก็บ indexของผู้เล่นที่ชนะในhistory

*__pattern__* เก็บ รูปแบบการชนะของผู้เล่นhistory

*__ishistory__* เก็บ booleanว่าเป็นhistory

*__calsquares__* คำนวนขนาดboardตามnum

*__winner__* คำนวนวิธีชนะตามขนาดของboard

## ฟังก์ชั่น

*__calculateWinner__* ใช้คำนวนผู้ชนะตามขนาดของboard

*__move__* คำนวนจุดที่เลือกและใช้เปลี่ยนตาของผู้เล่น

*__reset__* ใช้reset board

*__showpattern__* ใช้แสดงรูปแบบการชนะ

## Watcher

ดู winner และคำนวนว่ามี่การเปลี่ยนแปลงหรือไม่ถ้ามีให้เป็นhistoryลงlocalstorage

## Lifecycle Hooks

*__onMounted__* ใช้โหลด historyก่อน conponents จะถูกสร้างเสร็จ


## Algorithm

![Content Page (1)](https://github.com/permm/tictactoe/assets/89117732/774197ab-3602-40c4-b9be-ddb0c10ec924)
