# QR Codes

The wine portal generates qrcodes for users to print on their wine labels. By scanning the code, wine consumers can easily get access to all the details of a particular wine bottle, including vineyard maps, grape details, blend components, ingredients, irrigation practices and much more.

## Dependencies

- [**React QRCode Logo:**](https://www.npmjs.com/package/react-qrcode-logo) Typescript React component to generate a customizable QR Code.

## QR Code Generation

When a winery registers a new wine, after completing the mandatory form, a new high resolution QR Code is created. When scaned, the code prmpts a url + the wine's reference number. This url redirects the user to our dynamic wine-viewer route in our web application.

<div style="display:flex; align-items: center; gap: 24px; margin-top: 24px;">
    <img src="/images/qrcode.png" alt="qrcode" style="width:200px;"/>
    <div style="background: #33333344; padding: 16px; border-radius: 12px;">
        <p>https://wines.blazarlabs.io/tokenized-wine?ref=ARQ2Q-1716910554998<p/>
    </div>
</div>

## Code Repository

More details of the implemented code and components can be found in our [**github repository**](https://github.com/blazarlabs-io/wine-app/blob/develop/src/components/molecules/ReviewWine/index.tsx)
