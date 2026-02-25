# Definition & Logic

## Definitions (WIP)

* No.: 1
  * EN: Journey Settings
  * TW: 旅程設定
  * Definition (TW): 各種 Journey Level 的設定
  * Definition (EN): Settings for each Journey Level
* No.: 2
  * EN: Journey Flow
  * TW: 旅程流程
  * Definition (TW): 可以看到 Journey 全部的 Nodes 和 Node Paths 的視覺化呈現
  * Definition (EN): You can see a visual representation of all the Nodes and Node Paths of the Journey
* No.: 3
  * EN: Journey Condition
  * TW: 旅程條件
  * Definition (TW): Node 判斷條件
  * Definition (EN): Node determination conditions
* No.: 4
  * EN: Journey Node
  * TW: 旅程節點
  * Definition (TW): Journey 裡的流程方塊
  * Definition (EN): Flow boxes in the Journey
  * 4-1
    * EN: Trigger
    * TW: 觸發旅程
    * Definition (TW): 決定 Customer 是如何進入 Journey 的
    * Definition (EN): Determine how the Customer enters the Journey
  * 4-2
    * EN: Rule
    * TW: 規則
    * Definition (TW): 決定 Customer 的停止與前進、往哪裡去、何時結束
    * Definition (EN): Determines where the Customer stops and moves forward, where they go, and when they finish
    * 4-2-1
      * EN: Branch
      * TW: 分支
      * Definition (TW): 多個出口路線的 Node
      * Definition (EN): Node for multiple exit routes
    * 4-2-2
      * EN: Exit
      * TW: 旅程結束
      * Definition (TW): 決定 Customer 何時離開退出旅程
      * Definition (EN): Determines when the Customer leaves the exit journey
  * 4-3
    * EN: Action
    * TW: 動作
    * Definition (TW): 決定 Customer 會觸發什麼任務
    * Definition (EN): Determines what task the Customer will trigger
* No.: 5
  * EN: Node Path
  * TW: 節點路線
  * Definition (TW): Node 與 Node 之間的連接路線
  * Definition (EN): Node-to-Node connection routes
* No.: 6
  * EN: Node Filter
  * TW: 節點過濾器
  * Definition (TW): 額外的條件決定是否運作 Node 的邏輯，Conditions 只有一組條件\
    不支援：Branch Node、Exit Node
  * Definition (EN): Additional conditions determine whether to run the logic of the Node, have only one set of conditions\
    Not supported: Branch, Exit
* No.: 7
  * EN: Journey Goal
  * TW: 旅程目的
  * Definition (TW): Journey 的目的，可以設定在某個 Action (not in phase 1)
  * Definition (EN): The purpose of the Journey can be set in an Action (not in phase 1)

***

## Logic

* Topic: Logic
* Journey overview logic
  * Journey Flow 裡的每一個流程方塊都是 Node
  * Each flow box in a Journey Flow is a Node
* 一個完整合法的 Journey 至少會有一個 Trigger 跟 Exit
  * A complete legitimate Journey will have at least one Trigger and one Exit
* 每一個進入 Journey 的 Customer 最終都會走到 Exit 並退出 Journey
  * Every Customer entering a Journey will eventually go to the Exit and exit the Journey
* Branch
  * Branch 可以支援多組 Conditions，出口數=Conditions組數+1\
    e.g. view page -> view page A an/or/exclude page B or not
  * Branch can support multiple sets of Conditions, the number of exits = the number of Conditions + 1\
    e.g. view page -> view page A an/or/exclude page B or not
* Node
  * Node Filters 附加條件可以決定 Customer 是否會運作該 Node 的邏輯，支援一組 Conditions
    * Trigger 裡決定是否能進來
    * Wait 裡決定是否執行等待，不符合就會直接通過
  * Node Filters additional conditions can determine whether the Customer will run the logic of the Node, supporting one set of Conditions
    * Trigger: determines if it can come in
    * Wait: determines whether to perform a wait or not, and will pass if it does not.
* Condition
  * 一組 Conditions 最多五個條件
  * The maximum number of conditions in a set of Conditions is five.
* Goal
  * 完成 Journey Goal 的邏輯視為一次完成旅程 (not in phase 1)
  * The logic of completing a Journey Goal is considered a completed journey (not in phase 1)
* Rule
  * Friends don't stay inside the Rule node, they verify directly
* Trigger (notes)
  * The definition of Trigger is "those who meet the conditions, enter the journey, otherwise not", so tend to use words that are positive, such as "is" or "has"
  * Trigger node is for starting point; it's filter supported and up to 5 conditions can be included in 1 filter
  * Trigger must be the first point aka starting point. Therefore, when user click the "+" button on the path, the trigger node will not be displayed in the node list panel and cannot be added.
  * In the current planning, only 1 trigger is supported for a journey
* Rule (other)
  * Rule node can't be used in combination with filters
* Filter (note)
  * choose the "is not/ has not" instead of "exclude" in filter

***

## Limitation

* 一個 Filter 最多 5 個 Condition
  * A filter can have up to 5 conditions at most
* 一個 Journey 最多 30 個 Node
  * A journey can have up to 30 nodes at most
* 一個 Bot 最多 1000 個 Journey
  * A bot can have up to 1000 journeys at most
