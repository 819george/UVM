# UVM

example code [2.5.2](https://github.com/819george/UVM/tree/main/2.5.2)

- structrue  
<img src="https://github.com/819george/UVM/blob/main/images/UVM.png" width="400" height="240"/>

- env  
<img src="https://github.com/819george/UVM/blob/main/images/UVM_sequence.png" width="400" height="240"/>

- sequence_item_flow  
<img src="https://github.com/819george/UVM/blob/main/images/sequence_item_flow.png" width="320" height="360"/>

1. DUT: rxd 接收，再通過 txd 發送
2. Driver: 送一個封包  
透過 run_test 執行 main_phase、實例化 uvm_test_top，objection 取代 finish，  
type_id::create 實例化，config_db::set 配置、::get 取得,
3. transaction: 封包結構  
field_automation 不用自己寫 copy、compare、print
4. monitor: 不斷收集數據  
// unpack_bytes 只收動態數組
5. agent: 包含 drv、sqr、mon  
is_active == UVM_ACTIVE: input agent， UVM_PASSIVE: output agent  
6. env: i_agt、o_agt、mdl、scb
7. refernce model: 複製 i_agt 的 tr， 傳遞給 scb  
8. mycase0、mycase1: 方便切換不同的 sequence
- 問題  
connet phase 下到上: mdl、scb 建立 ap、blocking_get_port act_port 之後，在 env 用 fifo 連接
