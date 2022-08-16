<template>
  <!-- Start of the navbar -->
  <nav class="navbar position-sticky top-0 start-0 py-1 px-2">
    <!-- Content of the navbar -->
    <div class="content w-100 d-flex align-items-center">
      <!-- Logo -->
      <div class="logo d-flex align-items-center justify-content-xl-center">
        <img src="@/assets/images/icon.png" class="d-block" alt="logo" />
      </div>
      <!-- End of the logo -->

      <!-- Left side -->
      <div class="left-side d-flex align-items-center pe-2 pe-xl-0">
        <!-- Start of the search box -->
        <div class="search-box border-start border-2">
          <div
            class="w-50 search-box-container d-flex align-items-center position-relative"
          >
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

        <!-- Mobile dropdown -->
        <div class="dropdown d-lg-none me-3">
          <button
            class="btn text-white p-0 d-flex align-items-center justify-content-center dropdown-toggle border-0"
            type="button"
            data-bs-toggle="dropdown"
            aria-expanded="false"
          >
            <i class="fa-solid fa-bars"></i>
          </button>
          <ul class="dropdown-menu p-0">
            <li class="d-flex p-2 align-items-center border-bottom border-2">
              <!-- Start of the toggle-btn -->
              <div class="toggle-btn form-check form-switch ms-1 p-0">
                <input
                  class="form-check-input m-0"
                  type="checkbox"
                  id="themeBtn"
                />
              </div>

              <label for="themeBtn">مظهر داكن</label>
            </li>

            <li class="d-flex p-2 align-items-center border-bottom border-2">
              <!-- Start of the toggle-btn -->
              <i
                class="notification text-white ms-2 d-flex align-items-center justify-content-center fa-solid fa-bell"
              ></i>

              <span>الإشعارات</span>
            </li>

            <li class="d-flex p-2 align-items-center">
              <!-- Start of the toggle-btn -->
              <div class="profile-data d-flex align-items-center">
                <!-- Text data -->
                <div class="data ms-2">
                  <h6 class="name text-center mb-1">عبدالله</h6>
                  <h6 class="phone text-center mb-0">01015591833</h6>
                </div>

                <!-- profile image -->
                <img
                  src="@/assets/images/profile.png"
                  class="profile-img"
                  alt="profile-image"
                />
              </div>
            </li>
          </ul>
        </div>

        <!-- Start of the settings -->
        <div
          class="settings d-none d-lg-flex align-items-center justify-content-between pe-5"
        >
          <!-- Start of the toggle-btn -->
          <div class="toggle-btn form-check form-switch m-0 ms-2 p-0">
            <input class="form-check-input m-0" type="checkbox" id="themeBtn" />
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
    @media only screen and (max-width: 1400px) {
      width: 290px !important;
    }
    @media only screen and (max-width: 1200px) {
      width: fit-content !important;
    }
    img {
      height: 65px;
      width: 65px;
      object-fit: contain;
    }
  }
  .left-side {
    width: calc(100% - 315px);
    @media only screen and (max-width: 1400px) {
      width: calc(100% - 290px) !important;
    }
    @media only screen and (max-width: 1200px) {
      width: calc(100% - 65px) !important;
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
    .search-box {
      width: 70%;
      @media only screen and (max-width: 1200px) {
        width: 80%;
      }
      @media only screen and (max-width: 992px) {
        width: 95% !important;
        border: 0 !important;
      }
      .search-box-container {
        @media only screen and (max-width: 1200px) {
          width: 90% !important;
        }
        @media only screen and (max-width: 992px) {
          width: 100% !important;
        }
      }
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
    .dropdown-toggle {
      &::after {
        display: none !important;
      }
      &:focus {
        box-shadow: none !important;
      }
      i {
        font-size: 22px;
      }
    }
    .dropdown-menu {
      .toggle-btn {
        min-height: auto !important;
      }
      label,
      span {
        font: {
          size: 20px;
          weight: 500;
        }
      }
    }
    .settings {
      width: 30%;
      @media only screen and (max-width: 1200px) {
        width: 45% !important;
      }
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
