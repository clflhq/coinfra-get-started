# Get Started Coinfra

This is the example of using Coinfra API built on the Solana [Solana Web3 JavaScript API](https://docs.solana.com/developing/clients/javascript-api)

[Latest API Documentation](https://solana-labs.github.io/solana-web3.js/)

## Prerequisite

### Get Coinfra API key

Sign up [Coinfra](https://www.coinfra.io) and create a new project in order to get API key

### Install Solana Web3 JavaScript API

Refer to [here](https://github.com/solana-labs/solana-web3.js/blob/master/README.md#installation) for more detail

If you use the browser bundle, you don't have to install it

### Run Solana test validator

Install the latest Solana release from https://docs.solana.com/cli/install-solana-cli-tools

Use `solana-test-validator` command in order to run your test validator on your local machine

## Usage

### Use HTTP API

```js
const connectHttpApi = async function () {
  const connection = new solanaWeb3.Connection(
    "https://solana-devnet.coinfra.io/v1/<your-api-key>",
    "confirmed"
  );
  const block = await connection.getBalance(
    new solanaWeb3.PublicKey("<your-public-key>")
  );
  console.log("block");
  console.log(block);
};
connectHttpApi();
```

### Use WebSocket API

#### Connect
```js
connection = new solanaWeb3.Connection(
  "https://solana-devnet.coinfra.io/v1/<your-api-key>",
  {
    commitment: "confirmed",
    wsEndpoint: "wss://solana-devnet.coinfra.io/v1/<your-api-key>",
  }
);
```

#### Subscribe
```js
subscriptionId = connection.onSlotChange((slotInfo) => {
  console.log("subscribe slot info");
  console.log(slotInfo);
});
```

#### Unsubscribe
```js
try {
  await connection.removeSlotChangeListener(
    parseInt(document.querySelector("#subscriptionId").innerText)
  );
} catch (error) {
  console.log(error);
}
```

Refer to index.html of this repository for more detail

If you use Mac, the DocumentRoot of pre-installed Apache is /Library/WebServer/Documents

So you can access http://localhost after you save the index.html into /Library/WebServer/Documents

## Disclaimer

### Website Disclaimer

The information provided by Sharemall ("we," "us", or "our") on https://github.com/cifihg/coinfra get-started (the "Site") is for general informational purposes only.

All information on the Site is provided in good faith, however we make no representation or warranty of any kind, express or implied, regarding the accuracy, adequacy, validity, reliability, availability or completeness ofany information on the Site.

UNDER NO CIRCUMSTANCE SHALL WE HAVE ANY LIABILITY TO YOU FOR ANY LOSS OR DAMAGE OF ANY KIND INCURRED AS ARESULT OF THE USE OF THE SITE OR RELIANCE ON ANY INFORMATION PROVIDED ON THE SITE.

YOUR USE OF THE SITE AND YOUR RELIANCE ON ANY INFORMATION ON THE SITE IS SOLELY AT YOUR OWN RISK.

### External Links Disclaimer

The Site may contain (or you may be sent through the Site) links to other websites or content belonging to or originating from third parties or links to websites and features in banners or other advertising.

Such external links are not investigated, monitored, or checked for accuracy, adequacy, validity, reliability, availability or completeness by us.

WE DO NOT WARRANT, ENDORSE, GUARANTEE, OR ASSUME RESPONSIBILITY FOR THE ACCURACY OR RELIABILITY OF ANY INFORMATION OFFERED BY THIRD-PARTY WEBSITES LINKED THROUGH THE SITE OR ANY WEBSITE OR FEATURE LINKED IN ANY BANNER OR OTHER ADVERTISING.

WE WILL NOT BE A PARTY TO OR IN ANY WAY BE RESPONSIBLE FOR MONITORING ANY TRANSACTION BETWEEN YOU AND THIRD-PARTY PROVIDERS OF PRODUCTS OR SERVICES.

### Professional Disclaimer

The Site cannot and does not contain blockchain advice.

The blockchain information is provided for general informational and educational purposes only and is not a substitute for professional advice.

Accordingly, before taking any actions based upon such information, we encourage you to consult with the appropriate professionals.

We do not provide any kind of blockchain advice. T

HE USE OR RELIANCE OF ANY INFORMATION CONTAINED ON THE SITE IS SOLELY AT YOUR OWN RISK.
