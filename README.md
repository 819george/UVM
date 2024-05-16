# UVM

example code [2.5.2](https://github.com/819george/UVM/tree/main/2.5.2)

- structrue  
<img src="https://github.com/819george/UVM/blob/main/images/UVM.png" width="400" height="240"/>

- env  
<img src="https://github.com/819george/UVM/blob/main/images/UVM_sequence.png" width="400" height="240"/>

- sequence_item_flow  
<img src="https://github.com/819george/UVM/blob/main/images/sequence_item_flow.png" width="320" height="360"/>

1. DUT: rxd 接收，再通過 txd 發送
2. driver: 送一個封包  
透過 run_test 執行 main_phase、實例化 my_driver: uvm_test_top，objection 取代 finish，  
type_id::create 實例化，config_db::set 配置、::get 取得,
3. transaction: 封包結構  
field_automation 不用自己寫 copy、compare、print
4. monitor: 不斷收集數據  
unpack_bytes 只收動態數組
5. agent: 包含 drv、sqr、mon  
is_active == UVM_ACTIVE: input agent， UVM_PASSIVE: output agent  
6. env: i_agt、o_agt、mdl、scb
7. refernce model: 複製 i_agt 的 transaction，傳遞給 scb
  - TLM (monitor & model)
    - build phase 上到下: 
      - i_agt's monitor: analysis_port (ap)
      - model: blocking_get_port (act_port)，
    - connet phase 下到上:
      - 在 env 用 fifo 連接，因為 ap 為非阻塞需暫存
8. scoreboard: 比較 model 和 o_agt's monitor 的資料
  - TLM (類似 monitor & model)  
    - model (ap) & scoreboard (exp_port)
    - o_agt's monitor (ap) & scoreboard (act_port)
9. sequence: 創建 my_transaction 實例，在 body 中用 uvm_do 隨機化、傳給 squencer  
mycaseN 方便切換，在 agt 使用內建的端口連接  
  - uvm_driver: seq_item_port
  - uvm_sequencer: seq_item_export
10. TLM  
priority: PORT、EXPORT、IMP 高的可以連接低的  
action: put、get、transport 可以做不同動作  
    
