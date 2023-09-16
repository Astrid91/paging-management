# paging-management

根據使用者輸入的 input 檔，讀取方法種類、Page Frame 數量，以及
各個 Page Reference 的次序，以一維串列的方式儲存 process 相關資訊，並根
據不同的方法種類進行不同的 Page Replacement 方法。最後依據題目格式及檔
名要求寫入對應檔案，輸出檔中應包含依據 Page Reference 抵達次序而改變的
Page Frame，並標示是否進行 Page Fault，最後輸出 Page Fault、Page 
Replaces、Page Frames。
# 方法一：First In First Out (FIFO) 
FIFO 是根據 Page Reference 的次序來置換 Page Frame 裡的內容，當
有新的 Page Reference，會先查看 Page Frame 裡面是否有此 Reference，若有
的話則不需要再做置換，保持原本的 Page Frame；若無此 Reference 則將 Page 
Frame 中最先抵達的 Reference 移除，並將最新到達的 Reference 加入 Page 
Frame 中，若 Page Frame 還不滿最大的數量，則可以直接放入。
# 方法二：Least Recently Used (LRU) 
LRU 是先將過去歷史紀錄中最久沒被 Reference 到的 Page 置換掉，當
有新的 Page Reference，會先查看 Page Frame 裡面是否有此 Reference，若有
的話則不需要再做置換，將最新抵達的 Page Reference 移至 Page Frame 的最
前面；若無此 Reference 則檢查哪個 Page 最久沒被 Reference，並將其替換，
若 Page Frame 還不滿最大的數量，則可以直接放入。
# 方法三：Least Frequently Used (LFU) + FIFO 
LFU 是將過去歷史紀錄中最少被 Reference 到的 Page 置換掉，但此方
式有可能造成新進的 Page 不斷被置換掉的錯誤情形發生。當有新的 Page 
Reference，會先查看 Page Frame 裡面是否有此 Reference，若有的話則不需
要再做置換，保持原本的 Page Frame；若無此 Reference 則檢查哪個 Page 最
少被 Reference，並將其替換，若 Page Frame 還不滿最大的數量，則可以直接
放入。
# 方法四：Most Frequently Used (MFU) + FIFO 
MFU 跟 LFU 非常相似，是將最常被 Reference 到的 Page 置換掉，其餘
則和方法三相同。
# 方法五：LFU + LRU 
LFU 結合 LRU 的方式，會先檢查 Page Frame 中哪個 Page 被 Reference
的次數最少，若次數相同，則會根據 LRU 的規則來決定誰會被置換，也就是會
先置換掉過去歷史紀錄中最久沒被 Reference 到的 Page。
# 方法六：ALL 
方法六為方法一到五的集大成。
