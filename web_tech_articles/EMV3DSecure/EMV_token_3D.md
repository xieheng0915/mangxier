```
2.5.3 Processing Payment EMV Payment Tokens
General configuration:
In order for this specification to appropriately handle flows that initiate with EMV Payment Tokens, the Payment Token ranges shall be shared and configured on the appropriate DS. This is essential for the EMV Payment Token transaction to be routed to the appropriate DS and then to the ACS.
```
一般的な設定：
ペイメントトークンはDSサーバに共有また設定されるすべきのため、基本的にDSへ送ってさらにACSへ送信する。

```
EMV Payment Token handling during transaction flow:
During the Authentication Request (AReq) message flow, it might be necessary for the Payment Token to be detokenised and the actual PAN to be placed in the Cardholder Account Number for the remainder of the AReq flow. For instance, this could be required if the transaction initiated with an EMV Payment Token and the ACS was configure based off of the PAN. In this case, the EMV Payment Token Indicator in the AReq message is set to True to indicate that the transaction initiated with an EMV Payment Token.
```
トランザクションの中でEMVペイメントの処理：
必要ならAReqの中にデートークン化することも可能、ちなみにACSの方はPANだけで良い。ただし、該当トランザクションはペイメントトークンから始める場合はPTI＝Trueに設定する。
