<script>
  let images = [];
  let errors = { name: false, width: false, height: false };
  let width, height, name;
  let svgValue = `<svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
<g clip-path="url(#clip0_17_2)">
<path fill-rule="evenodd" clip-rule="evenodd" d="M14 4.5V14C14 14.5304 13.7893 15.0391 13.4142 15.4142C13.0391 15.7893 12.5304 16 12 16V15C12.2652 15 12.5196 14.8946 12.7071 14.7071C12.8946 14.5196 13 14.2652 13 14V4.5H11C10.6022 4.5 10.2206 4.34196 9.93934 4.06066C9.65804 3.77936 9.5 3.39782 9.5 3V1H4C3.73478 1 3.48043 1.10536 3.29289 1.29289C3.10536 1.48043 3 1.73478 3 2V11H2V2C2 1.46957 2.21071 0.960859 2.58579 0.585786C2.96086 0.210714 3.46957 0 4 0L9.5 0L14 4.5ZM0 14.841C0.00572468 14.9986 0.0443598 15.1532 0.113421 15.2949C0.182483 15.4367 0.280442 15.5624 0.401 15.664C0.531 15.772 0.689 15.856 0.879 15.916C1.069 15.977 1.29 16.007 1.544 16.007C1.882 16.007 2.168 15.954 2.402 15.849C2.639 15.744 2.818 15.597 2.942 15.409C3.06811 15.2138 3.13321 14.9854 3.129 14.753C3.129 14.529 3.084 14.343 2.994 14.193C2.90251 14.0431 2.77317 13.92 2.619 13.836C2.44219 13.7382 2.25175 13.6675 2.054 13.626L1.433 13.482C1.28626 13.4553 1.14767 13.395 1.028 13.306C0.982558 13.2707 0.945972 13.2253 0.921148 13.1734C0.896325 13.1215 0.883947 13.0645 0.885 13.007C0.885 12.851 0.946 12.723 1.069 12.623C1.194 12.522 1.365 12.471 1.582 12.471C1.725 12.471 1.848 12.494 1.952 12.539C2.04734 12.5782 2.13151 12.6404 2.197 12.72C2.25855 12.7942 2.29988 12.8831 2.317 12.978H3.067C3.05481 12.7745 2.98588 12.5784 2.868 12.412C2.74161 12.2325 2.56877 12.0908 2.368 12.002C2.12244 11.8943 1.85604 11.8424 1.588 11.85C1.295 11.85 1.036 11.9 0.812 12C0.587 12.099 0.412 12.24 0.284 12.421C0.157 12.603 0.094 12.816 0.094 13.06C0.094 13.261 0.134 13.436 0.217 13.584C0.299 13.733 0.416 13.854 0.568 13.951C0.721 14.046 0.9 14.118 1.108 14.164L1.726 14.308C1.933 14.357 2.086 14.421 2.188 14.501C2.23802 14.5389 2.27808 14.5883 2.30473 14.6451C2.33138 14.7019 2.34383 14.7643 2.341 14.827C2.34249 14.93 2.31287 15.0311 2.256 15.117C2.19134 15.2049 2.10235 15.272 2 15.31C1.889 15.357 1.751 15.38 1.587 15.38C1.47 15.38 1.363 15.367 1.267 15.34C1.17859 15.3155 1.09481 15.2767 1.019 15.225C0.952427 15.1819 0.895433 15.1256 0.851564 15.0595C0.807694 14.9935 0.777888 14.9191 0.764 14.841H0ZM4.575 15.931H5.527L6.854 11.932H5.975L5.088 15.07H5.05L4.153 11.932H3.236L4.575 15.932V15.931ZM10.058 12.638C10.134 12.79 10.181 12.954 10.198 13.13H9.422C9.40422 13.0422 9.37177 12.958 9.326 12.881C9.28165 12.8076 9.22399 12.7432 9.156 12.691C9.08577 12.6343 9.00532 12.5915 8.919 12.565C8.82195 12.5346 8.7207 12.5197 8.619 12.521C8.335 12.521 8.113 12.621 7.955 12.823C7.798 13.023 7.72 13.307 7.72 13.673V14.17C7.72 14.405 7.753 14.61 7.817 14.786C7.87541 14.9509 7.98158 15.0947 8.122 15.199C8.2749 15.3012 8.45624 15.3523 8.64 15.345C8.79798 15.3506 8.95491 15.3173 9.097 15.248C9.21142 15.1884 9.30621 15.0971 9.37 14.985C9.43 14.875 9.46 14.755 9.46 14.621V14.367H8.637V13.777H10.213V14.575C10.213 14.768 10.181 14.952 10.117 15.125C10.0529 15.2964 9.95298 15.4522 9.824 15.582C9.68359 15.7212 9.51472 15.8283 9.329 15.896C9.131 15.97 8.899 16.007 8.631 16.007C8.37414 16.0122 8.11873 15.9674 7.879 15.875C7.67457 15.7917 7.49191 15.6628 7.345 15.498C7.19891 15.3294 7.09019 15.1317 7.026 14.918C6.95335 14.6764 6.91794 14.4252 6.921 14.173V13.666C6.921 13.306 6.987 12.989 7.12 12.717C7.254 12.446 7.449 12.235 7.703 12.084C7.959 11.932 8.267 11.856 8.629 11.856C8.867 11.856 9.079 11.889 9.264 11.956C9.452 12.022 9.612 12.114 9.744 12.231C9.878 12.348 9.982 12.484 10.058 12.638V12.638Z" fill="black"/>
</g>
<defs>
<clipPath id="clip0_17_2">
<rect width="16" height="16" fill="white"/>
</clipPath>
</defs>
</svg>
`;

  function svg2img() {
    var svg64 = btoa(svgValue);
    var b64start = "data:image/svg+xml;base64,";
    var image64 = b64start + svg64;
    images = [...images, { src: image64, width, height, name }];
  }
  function base64SvgToBase64Png(originalBase64, width, height) {
    return new Promise((resolve) => {
      let img = document.createElement("img");
      img.onload = function () {
        document.body.appendChild(img);
        let canvas = document.createElement("canvas");
        document.body.removeChild(img);
        canvas.width = width;
        canvas.height = height;
        let ctx = canvas.getContext("2d");
        ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
        try {
          let data = canvas.toDataURL("image/png");
          resolve(data);
        } catch (e) {
          resolve(null);
        }
      };
      img.onerror = function () {
        resolve(null);
      };
      img.src = originalBase64;
    });
  }
  function addImage(e) {
    errors = { width: !width, height: !height, name: !name };
    if (Object.values(errors).some((err) => err)) {
      return;
    }
    svg2img();
    width = "";
    height = "";
    name = "";
  }

  async function downloadImages() {
    images.forEach(async (img) => {
      const pngUrl = await base64SvgToBase64Png(img.src, img.width, img.height);
      const a = document.createElement("a");
      a.setAttribute("download", `${img.name}-${img.width}x${img.height}`);
      a.setAttribute("href", pngUrl);
      document.body.appendChild(a);
      document.querySelector("a").click();
      document.body.removeChild(a);
    });
  }

  function removeImage(e, index) {
    console.log(e.target.parentNode);
    e.target.parentNode.classList.add("delete-aniamtion");
    // images.splice(index, 1);
    // images = [...images];
  }
</script>

<main>
  <h2 style="font-size:48px">SVG2IMG</h2>
  <div class="form">
    <input
      class="svg-input"
      placeholder="SVG goes here..."
      bind:value={svgValue}
    />
    <div class="flex">
      <input
        style="border:1px solid {errors.name && 'red'}"
        bind:value={name}
        type="text"
        placeholder="Image name"
      />
      <input
        style="border:1px solid {errors.width && 'red'}"
        bind:value={width}
        type="number"
        placeholder="Width"
      />
      <input
        style="border:1px solid {errors.height && 'red'}"
        bind:value={height}
        type="number"
        placeholder="Height"
      />
      <button style="padding:14px" on:click={addImage}>Generate PNG</button>
    </div>
  </div>
  {#if images.length}
    <div class="footer">
      <div>
        {#each images as image, index}
          <div class="image-container">
            <div class="size-rebon">{image.width}x{image.height}</div>
            <div on:click={(e) => removeImage(e, index)} class="delete-btn">
              X
            </div>

            <img src={image.src} width={75} height={75} alt="downloable" />
          </div>
        {/each}
      </div>
      <button on:click={() => downloadImages()} class="download-btn"
        >Download</button
      >
    </div>
  {/if}
</main>

<style>
  main {
    display: flex;
    flex-direction: column;
    height: 100vh;
    align-items: center;
    justify-content: center;
  }
  .form {
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
  }
  .svg-input {
    flex: 1;
    padding: 20px;
  }
  .flex {
    display: flex;
    align-items: center;
  }
  input {
    padding: 17px;
    border-radius: 6px;
    border: 1px solid rgba(144, 144, 144, 0.3);
  }
  .footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    position: absolute;
    bottom: 0;
    height: 120px;
    border-top: 1px solid rgba(144, 144, 144, 0.2);
    width: 100%;
    padding: 0 20px;
  }
  .footer > div {
    display: flex;
    height: 100%;
  }
  .image-container {
    padding: 14px;
    border-right: 1px solid rgba(144, 144, 144, 0.2);
    position: relative;
    margin-right: 16px;
  }
  .size-rebon {
    background-color: rgb(232, 231, 231);
    position: absolute;
    width: 100%;
    height: 30px;
    bottom: 0;
    overflow: hidden;
    right: 0px;
  }

  .delete-btn {
    position: absolute;
    border-radius: 50px;
    border: 3px solid white;
    background-color: red;
    top: 0;
    right: 0;
    width: 25px;
    height: 25px;
    color: white;
    font-weight: 700;
    text-align: center;
    cursor: pointer;
    margin-right: 24px;
  }

  .flex > * {
    margin-top: 12px;
    margin-right: 12px;
  }
  .flex > button {
    margin-right: 0;
  }
  .delete-aniamtion {
    animation: fade 10s;
    opacity: 0;
  }
  @keyframes fade {
    from {
      opacity: 1;
    }
    to {
      opacity: 0;
    }
  }
</style>
