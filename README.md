# UVM

example code [2.5.2](https://github.com/819george/UVM/tree/main/2.5.2)

- structrue  
<img src="https://github.com/819george/UVM/blob/main/images/UVM.png" width="350" height="210"/>

- env  
<img src="https://github.com/819george/UVM/blob/main/images/UVM_sequence.png" width="350" height="210"/>

- sequence_item_flow  
<img src="https://github.com/819george/UVM/blob/main/images/sequence_item_flow.png" width="240" height="270"/>

1. DUT：rxd接收，再通過txd發送
2. Driver：送一個封包
透過run_test 執行main_phase、實例uvm_test_top，objection取代finish，
type_id::create實例化，config_db::set配置、::get取得,
3. transaction:封包結構
field_automation不用自己寫copy、compare、print
4. monitor:不斷收集數據
//unpack_bytes只收動態數組
5. agent:包含drv、sqr、mon
is_active == UVM_ACTIVE: input agent， UVM_PASSIVE: output agent

6. env: i_agt、o_agt、mdl、scb
7. refernce model:複製i_agt的tr， 傳遞給scb  

- 問題  
connet phase下到上:mdl、scb建立ap、blocking_get_port act_port之後，在env用fifo連接
