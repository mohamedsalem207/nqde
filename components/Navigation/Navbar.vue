<template>
  <!-- Start of the navbar -->
  <nav class="navbar position-sticky top-0 start-0 py-1 px-2">
    <!-- Content of the navbar -->
    <div class="content w-100 d-flex align-items-center">
      <!-- Logo -->
      <div class="logo d-flex align-items-center justify-content-center">
        <img src="@/assets/images/icon.png" class="d-block" alt="logo" />
      </div>
      <!-- End of the logo -->

      <!-- Left side -->
      <div class="left-side d-flex align-items-center">
        <!-- Start of the search box -->
        <div class="search-box border-start border-2">
          <div class="w-50 d-flex align-items-center position-relative">
            <input
              type="text"
              class="form-control"
              placeholder="ما الذى تبحث عنه ؟"
            />
            <i
              class="search-icon fa-solid fa-magnifying-glass position-absolute"
            ></i>
          </div>
        </div>
        <!-- End of the search box -->

        <!-- Start of the settings -->
        <div
          class="settings d-flex align-items-center justify-content-between pe-5"
        >
          <!-- Start of the toggle-btn -->
          <div class="toggle-btn form-check form-switch m-0 ms-2 p-0">
            <input
              class="form-check-input m-0"
              type="checkbox"
              id="flexSwitchCheckChecked"
            />
          </div>
          <!-- End of the toggle-btn -->

          <!-- Notification -->
          <i
            class="notification text-white ms-2 d-flex align-items-center justify-content-center fa-solid fa-bell"
          ></i>
          <!-- End of the notification -->

          <!-- Profile data -->
          <div class="profile-data d-flex align-items-center">
            <!-- Text data -->
            <div class="data ms-2">
              <h6 class="name text-white text-center mb-1">عبدالله</h6>
              <h6 class="phone text-white text-center mb-0">01015591833</h6>
            </div>

            <!-- profile image -->
            <img
              src="@/assets/images/profile.png"
              class="profile-img"
              alt="profile-image"
            />
          </div>
          <!-- End of the profile data -->
        </div>
        <!-- End of the settings -->
      </div>
    </div>
    <!-- End of the content of the navbar -->
  </nav>
  <!-- End of the navbar -->
</template>

<script>
export default {
  name: 'Navbar',
}
</script>

<style lang="scss" scoped>
.navbar {
  background-color: #042f4d;
  z-index: 101;
  .logo {
    width: 315px;
    img {
      height: 65px;
      width: 65px;
      object-fit: contain;
    }
  }
  .left-side {
    width: calc(100% - 315px);
    .search-box {
      width: 70%;
      border-color: #a3a3a3 !important;
      input {
        border-radius: 10px;
        font: {
          size: 18px;
          weight: bold;
        }
      }
      .search-icon {
        color: #a3a3a3;
      }
    }
    .settings {
      width: 30%;
      .toggle-btn {
        .form-check-input {
          height: 28px;
          width: 58px;
          background-size: 35px;
          cursor: pointer;
          &:focus {
            box-shadow: none;
          }
        }
      }
      .notification {
        width: 28px;
        height: 28px;
        background-color: #f20505;
        border-radius: 50%;
        cursor: pointer;
      }
      .profile-img {
        height: 45px;
        width: 45px;
        border-radius: 50%;
      }
    }
  }
}
html[dir='rtl'] .search-icon {
  left: 10px;
}
html[dir='ltr'] .search-icon {
  right: 10px;
}
</style>
