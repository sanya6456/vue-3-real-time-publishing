<template>
  <div class="fluid-container">
    <div class="row">
      <div class="col-3">
        <!--  left side menu -->
        <div class="left-menu mt-3">
          <div class="left-side-groups px-2 py-2 d-flex">
            <div class="profile-picture">
              <img :src="user.profilePicture" />{{ user.firstName }}
              {{ user.lastName }}
            </div>
          </div>
          <!--User profile-->
          <div
            class="left-side-groups px-2 py-2 d-flex"
            v-for="grp in groups"
            :key="grp.id"
          >
            <div v-html="grp.menuIcon" class="menu-icons"></div>
            {{ grp.menuItem }}
          </div>
          <!--Left side navigation-->
          <button class="btn btn-dark btn-block see-more">
            see more <i class="fas fa-chevron-down pl-2 text-light"></i>
          </button>
          <!--see more button-->
        </div>
      </div>
      <div class="col-6">
        <!-- Stories -->
        <div class="stories">
          <div class="pic-container">
            <img :src="user.profilePicture" />
            <p class="img-text">{{ `${user.firstName} ${user.lastName}` }}</p>
          </div>
          <div
            class="pic-container"
            v-for="storyImg in stories"
            :key="storyImg.story"
          >
            <img :src="storyImg.story" />
            <p class="img-text">{{ storyImg.name }}</p>
          </div>
        </div>
        <!--  Input field (publish a post) -->
        <div class="post-input mt-3 mb-5 d-flex">
          <div class="small-prof-pic">
            <img :src="user.profilePicture" />
          </div>

          <input
            type="text"
            class="input-text"
            v-model="inputValue"
            @keyup.enter="addNewPost"
          />

        </div>
        <div class="published-posts" v-for="post in posts" :key="post.content">
          <div class="name-date d-flex flex-space-between my-auto justify-content-between">
            <p class="post-username my-auto"><img :src="user.profilePicture"> {{post.authorsName}}</p>
            <p class="post-date my-auto">{{post.date}}</p>
          </div>
            <p class="post-content my-4">{{post.content}}</p>
        </div>
      </div>
      <div class="col-3"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Grids",
  data() {
        var d=new Date();
        var dd=d.getDate();
        var mm=d.getMonth();
        var yyyy=d.getFullYear();
        var hour=d.getHours();
        var min=d.getMinutes();
        d=`${dd}-${mm}-${yyyy} ${hour}:${min}`;
    return {
      followers: 0,
      date: d,
      user: {
        id: 1,
        profilePicture: require("../assets/profile-01.png"),
        userName: "Jessica_6456",
        firstName: "Jessica",
        lastName: "Blaum",
        email: "jessica.blaum@gmail.com",
        isAdmin: true,
        description: [
          { id: 1, content: "First line description" },
          { id: 2, content: "Second line description" },
        ],
      },
      groups: [
        {
          id: "1",
          menuItem: "COVID-19 Inform Center",
          menuIcon: `<i class="fas fa-head-side-mask text-danger"></i>`,
        },
        {
          id: "2",
          menuItem: "Pages",
          menuIcon: `<i class="far fa-flag text-warning"></i>`,
        },
        {
          id: "3",
          menuItem: "Friends",
          menuIcon: `<i class="fas fa-user text-success"></i>`,
        },
        {
          id: "4",
          menuItem: "Messenger",
          menuIcon: `<i class="fab fa-facebook-messenger text-primary"></i>`,
        },
        {
          id: "5",
          menuItem: "Memories",
          menuIcon: `<i class="far fa-clock text-info"></i>`,
        },
        {
          id: "6",
          menuItem: "Videos",
          menuIcon: `<i class="fas fa-video text-success"></i>`,
        },
      ],

      stories: [
        { story: require("../assets/profile-02.jpg"), name: "Claudia Aumit" },
        {
          story: require("../assets/profile-04.jpg"),
          name: "Franchisca Leudin",
        },
        {
          story: require("../assets/profile-05.jpg"),
          name: "Georgina Amberreria",
        },
        { story: require("../assets/profile-06.jpg"), name: "Amber Klaudia" },
      ],

      inputValue: "",
      posts:[
          {
            content:"This is my first post! I would like to have a diner with my friends, in the nearest restaurant. My preferabel meat is turky!",
            authorsName:"Jessica_6456",
            date: d,
          },
      ],
    };
  },
          
  methods: {
      addNewPost(){
          this.posts.push({content: this.inputValue, authorsName: this.user.userName, date: this.date});

          console.log(this.posts);
          this.inputValue="";
      },

  },

};
</script>

<style lang="scss">
//container
.fluid-container {
  min-height: 100vh;
  background-color: #000000;
  color: #fff;
}

//left menu
.left-menu {
  .left-side-groups {
    font-size: clamp(0.7rem, 1.5vw, 1.4rem);
    i{
        font-size: 1.4rem;
        @media only screen and(max-width:1050px) {
            font-size: 1.1rem;
        }
    }
    .profile-picture {
      padding-left: 1rem;
      @media only screen and(max-width:900px) {
        padding-right: 1.2rem;
      }
      img {
        width: 1.5rem;
        height: 1.5rem;
        border-radius: 360%;
        margin-right: 1.8rem;
        @media only screen and(max-width:900px) {
          margin-right: 1.2rem;
        }
        @media only screen and(max-width:1050px) {
            width: 1.2rem;
            height: 1.2rem;
        }
      }
    }
    .menu-icons {
      padding-left: 1rem;
      padding-right: 1.8rem;
      @media only screen and(max-width:900px) {
        padding-right: 1.2rem;
      }
    }
  }
  .see-more {
    font-size: clamp(0.6rem, 1vw, 1.5rem);
  }
}

//stories
.stories {
  max-height: 17rem;
  margin: auto;
  display: flex;
  justify-content: space-between;
  .pic-container {
    position: relative;
    width: 18%;
    height: auto;
    margin: 2rem 0 1rem 0;

    border-radius: 16px;
    border: 1px solid #fff;

    img {
      width: 100%;
      height: 100%;
      border-radius: 16px;
    }
    p {
      position: absolute;
      bottom: 0;
      left: 0;
      color: #fff;
      z-index: 100;
      margin: 0;
      padding: 0 0.5rem;
      font-size: clamp(0.6rem, 1vw, 1rem);
    }
  }
}

//input field (publish post)
.post-input {
  .input-text {
    border-radius: 32px;
    width: 100%;
    height: auto;
    padding: 0.2rem 1rem;
    margin: auto 0 auto auto;
    background-color: rgb(194, 194, 194);
    font-size: clamp(0.8rem, 1.5vw, 1.5rem);
    &:focus{
        background-color: #fff;
    }
  }
  .small-prof-pic {
    img {
      width: 3.2rem;
      height: 3.2rem;
      border-radius: 360%;
      margin-right: 1rem;
    }
  }
}

.published-posts{
    color: #fff;
    .post-username{
      font-size: clamp(0.8rem, 1.5vw, 1.4rem);
      img{
        width: 3.2rem;
        height: 3.2rem;
        border-radius: 360%;
        margin-right: 1rem;
      }
    }
}
</style>
