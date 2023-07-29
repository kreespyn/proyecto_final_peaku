<template>
    <b-container fluid class="px-5">
      <b-row class="px-0" style="background: #FEFCFB;">
        <b-col cols="12" class="mx-0 pt-0">
          <b-navbar toggleable="lg" type="light" variant="light">
            <b-navbar-brand href="#"><b-img :src="require('@/assets/Logo.png')" alt="Logo" /></b-navbar-brand>
            <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
            <b-collapse id="nav-collapse" is-nav>
              <b-navbar-nav class="d-flex justify-content-center w-100 mx-5">
                <b-nav-item class="mx-0">Home</b-nav-item>
                <b-nav-item class="mx-0">About</b-nav-item>
                <b-nav-item class="mx-0">Destination</b-nav-item>
                <b-nav-item class="mx-0">Tour</b-nav-item>
                <b-nav-item class="mx-0">Blog</b-nav-item>
              </b-navbar-nav>
              <b-navbar-nav class="ml-auto d-flex w-50">
                <b-button variant="outline-primary" class="mx-4 login" style="color:#fa7436;border: 1px;">Login</b-button>
                <b-button variant="primary" class="mx-0" style="background-color: #fa7436; border:none;">Sign Up</b-button>
              </b-navbar-nav>
            </b-collapse>
          </b-navbar>
        </b-col>
      </b-row>
    </b-container>
  </template>

  <style scoped>
  .login:hover,
  .login:focus,
  .login:active {
    background-color: transparent !important;
    border-color: #fa7436 !important;
  }
  </style>