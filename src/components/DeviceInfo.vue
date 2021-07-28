<template>
  <div>
    <section class="header-bg">
      <h3 class="device-info">DEVICE INFO</h3>
    </section>
    <section>
      <div class="device-info__details">
        <table class="table table-striped table-hover">
          <thead>
            <tr>
              <th scope="col" colspan="2" class="table-heading">Resolution</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>Width</td>
              <td>{{ deviceWidth }}</td>
            </tr>
            <tr>
              <td>Height</td>
              <td>{{ deviceHeight }}</td>
            </tr>
            <tr>
              <td>Orientation</td>
              <td>{{ deviceOrientation }}</td>
            </tr>
            <tr>
              <td>Device Pixel Ratio</td>
              <td>{{ devicePixelRation }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </section>
    <footer>
      <p>
        Device Info Source code -
        <a href="https://github.com/ktrajasekar/deviceinfo.git" target="_blank">
          Deviceinfo</a
        >
      </p>
    </footer>
  </div>
</template>

<script>
export default {
  name: "Deviceinfo",
  data() {
    return {
      deviceWidth: null,
      deviceHeight: null,
      deviceOrientation: null,
      devicePixelRation: null,
    };
  },
  methods: {
    initDeviceInfo() {
      this.deviceWidth = screen.width;
      this.deviceHeight = screen.height;
      this.devicePixelRation = window.devicePixelRatio;
      if (window.orientation === 90 || window.orientation === -90) {
        this.deviceOrientation = "Landscape";
      } else {
        this.deviceOrientation = "Portrait";
      }
    },
  },
  mounted: function() {
    this.initDeviceInfo();
    window.addEventListener("resize", this.initDeviceInfo);
    window.addEventListener("orientationchange", this.initDeviceInfo);
  },
  destroyed() {
    window.removeEventListener("resize", this.initDeviceInfo);
    window.removeEventListener("orientationchange", this.initDeviceInfo);
  },
};
</script>
