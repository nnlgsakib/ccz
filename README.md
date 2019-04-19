# infura-explorer

```
          ██╗███╗   ██╗███████╗██╗   ██╗██████╗  █████╗           
          ██║████╗  ██║██╔════╝██║   ██║██╔══██╗██╔══██╗          
█████╗    ██║██╔██╗ ██║█████╗  ██║   ██║██████╔╝███████║    █████╗
╚════╝    ██║██║╚██╗██║██╔══╝  ██║   ██║██╔══██╗██╔══██║    ╚════╝
          ██║██║ ╚████║██║     ╚██████╔╝██║  ██║██║  ██║          
          ╚═╝╚═╝  ╚═══╝╚═╝      ╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═╝          
                                                                  
███████╗██╗  ██╗██████╗ ██╗      ██████╗ ██████╗ ███████╗██████╗  
██╔════╝╚██╗██╔╝██╔══██╗██║     ██╔═══██╗██╔══██╗██╔════╝██╔══██╗ 
█████╗   ╚███╔╝ ██████╔╝██║     ██║   ██║██████╔╝█████╗  ██████╔╝ 
██╔══╝   ██╔██╗ ██╔═══╝ ██║     ██║   ██║██╔══██╗██╔══╝  ██╔══██╗ 
███████╗██╔╝ ██╗██║     ███████╗╚██████╔╝██║  ██║███████╗██║  ██║ 
╚══════╝╚═╝  ╚═╝╚═╝     ╚══════╝ ╚═════╝ ╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝ 
```

...is an Ethereum block explorer that updates in real-time by hooking into Infura's websocket API. It is written in `Typescript`, uses `React v16.18`.
It manages Web3 data in the App state by using React's `useReducer` Hooks wrapped in `Context` higher-order components to bless any component with direct access to anything it needs.

## Getting started
1) Make sure you have:
    * `node v10.13.0+`
    * `npm | yarn`
    * `a computer`
2) Clone this repository
3) `cd <CLONED_DIRECTORY>`
4) `yarn` if you're of persuarion, else `npm i`

### Building and running
```bash
$ npm run buiild && npm run start:prod
```

### Running dev mode
Just FYI, this causes pretty bad flashes of unstyled content.
```bash
$ npm start
```


## Notes
* Operates one block behind current block
  * Temporary fix because sometimes calling `web3.eth.getBlock(BLOCK_NUMER)` for the newest block would return `null`.
* Doesn't reconnect to websocket if it closes after inactivity (Infura disconnects after 1 hour unless pinged).
* Performane goes down the more blocks you load after clicking `LOAD MORE` or `SHOW NEW BLOCKS`.
* First app I've ever seen that opening React DevTools will cause to become non-responsive.
  * It's probably because of the thousands of `<divs />` for the tranaction squares.
  * _Pretty dang smooth otherwise..._

## TO-DO
* Add `# MORE TXs` at the bottom of the block cards when over TX count is >100.
* Add ability to expand card to view overflow transactions.
* Add more tests (only 1 right now, sorry :[).
* Verify that the stats in the header are calculated correctly.