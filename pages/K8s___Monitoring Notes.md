category:: Kubernetes
type:: #K8s, #Monitoring
alias:: K8s - Monitoring - Notes

- ## Probe 的參數設定
- |參數|描述|預設值|
  |--|--|--|
  |initialDelaySeconds|container 運行後 probe 才開始運作|0|
  |periodSeconds|Probe 的檢查間隔時間|10|
  |timeoutSeconds|Probe 等待時間視為超時|1|
  |successThreshold|在失敗後，必須連續滿足幾次 Probe 偵測存活才視為服務成功運行|1|
  |failureThreshold|偵測失敗的累計次數，超過此數值，即視為放棄服務重啟 container|3|