## A basic description how does randomness fulfillment works

1. controller.chainlisten.VORCoordinatorListener.StartPoll recursively calls *.Request sends requests to eth to check if new transactions came up
2. *.Request checks if there is a randomnessRequest (check if the tx is randomnessRequest by signature), addressed to Oracle (checks by keyHash)
3. when request is found *.Request takes seed (converted to byte), blockHash and blockNumber, then sends them to service.Service.FulfillRandomness
4. *.FulfillRandomness builds preSeed generates secretKey from private key (LN [19:22]) and sends secretKey and preSeed to vor.GenerateProofResponse
5. vor.GenerateProofResponse returns the marshaled proof of the VOR output back to *.FulfillRandomness 
6. *.FulfillRandomness returns transaction info and errors back to *.Request
7. *.Request saves data to database
8. *.Request continues to iterate through transactions and repeats if one more transaction is found