<script lang="ts">
export default {
  name: "Form",

  data() {
    return {
      nameInput: '',
      imageInput: '',
      amountVolumes: 1,
      volumeInput: [
        {host: '', container: ''}
      ],
      amountPorts: 1,
      portInput: [
        {host: '', container: ''}
      ]
    }
  },

  methods: {
    generateOutput() {
      console.log("start generate");
      console.log(`Name: ${this.nameInput}`);
      console.log(`Image: ${this.imageInput}`);
      console.log(`Volume: `, this.volumeInput);
      console.log(`Port: `, this.portInput);

      // this.testMethod();
    },
    addVolumeInput() {
      this.volumeInput.push(
        {host: '', container: ''}
      );
      this.amountVolumes++;
    },
    addPortInput() {
      this.portInput.push(
        {host: '', container: ''}
      );
      this.amountPorts++;
    }
  }
}
</script>

<template>
  <form>
    <div class="mb-3">
      <label for="nameInput" class="form-label">Name</label>
      <input type="text" class="form-control" id="nameInput" placeholder="application" v-model="nameInput" required>
    </div>

    <div class="mb-3">
      <label for="imageInput" class="form-label">Image</label>
      <select class="form-select" id="imageInput" v-model="imageInput" aria-label="Image" required>
        <option>- select image -</option>
        <option value="nodejs-2.18-apache-bullsyey">thecodingmachine/nodejs:v2-18-apache-bullseye</option>
      </select>
    </div>

    <div class="mb-3">
      <label class="form-label">Volumes</label>
      <div class="border border-secondary p-4">
        <div class="row">
          <div class="col-6">Host</div>
          <div class="col-6">Container</div>
        </div>

        <div class="row" v-for="index in amountVolumes">
          <div class="col-6">
            <input type="text" class="form-control" v-model="volumeInput[index-1]['host']" placeholder="./ssh">
          </div>
          <div class="col-6">
            <input type="text" class="form-control" v-model="volumeInput[index-1]['container']" placeholder="/home/.ssh">
          </div>
        </div>

        <span @click="addVolumeInput" class="btn btn-success w-100 mt-3"> + </span>
      </div>
    </div>

    <div class="mb-3">
      <label class="form-label">Ports</label>
      <div class="border border-secondary p-4">
        <div class="row">
          <div class="col-6">Host</div>
          <div class="col-6">Container</div>
        </div>

        <div class="row" v-for="index in amountPorts">
          <div class="col-6">
            <input type="text" class="form-control" v-model="portInput[index-1]['host']" placeholder="443">
          </div>
          <div class="col-6">
            <input type="text" class="form-control" v-model="portInput[index-1]['container']" placeholder="443">
          </div>
        </div>

        <span @click="addPortInput" class="btn btn-success w-100 mt-3"> + </span>
      </div>
    </div>

    <span @click="generateOutput" class="btn btn-primary">generate</span>
  </form>
</template>
