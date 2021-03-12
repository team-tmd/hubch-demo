<template>
  <div>
    <div>
      <div v-if="user.uid" key="sign-in">
        [{{ (user.profile, user.displayName) }}]
        <button type="button" @click="signOut">Sign out</button>
      </div>
      <div v-else key="sign-out">
        <button type="button" @click="signIn">Sign in</button>
      </div>
    </div>
  </div>
</template>

<script>
import firebase from "firebase"
export default {
  data() {
    return {
      user: "",
    }
  },

  created() {
    firebase.auth().onAuthStateChanged((user) => {
      this.user = this.user ? user : {}
      // if(user){
      //   this.getUserInfo(snapchat)
      // }
    })
  },

  methods: {
    //Sign in
    signIn() {
      let provider = new firebase.auth.GoogleAuthProvider()
      firebase
        .auth()
        .signInWithPopup(provider)
        // .then(this.users getProffilePicUrl)
        .then(this.getUsersName)
    },
    //Sign out
    signOut() {
      firebase.auth().signOut()
    },
    //Initial Firebase Auth.
    // initFirebaseAuth() {
    //   firebase.auth().onAuthStateChanged(authStateObserber)
    // },

    //Returns the signed-in user's profile pic URL.
    getProffilePicUrl() {
      return firebase.auth().currentUser.photoURL //|| "images/profile_placeholder.png"
    },
    //Returns the signed-in user's display name
    getUsersName() {
      return firebase.auth().currentUser.displayName
    },
    isUserSignedIn() {
      return !!firebase.auth().currentUser
    },
  },
}
</script>
