<!-- Firebase SDKs -->
<script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-auth-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore-compat.js"></script>

<script>
  const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_PROJECT.firebaseapp.com",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_PROJECT.appspot.com",
    messagingSenderId: "YOUR_SENDER_ID",
    appId: "YOUR_APP_ID"
  };
  firebase.initializeApp(firebaseConfig);
</script>

const db = firebase.firestore();
const movieList = document.getElementById('movie-list');

// Dummy login
firebase.auth().signInWithEmailAndPassword('user@example.com', 'password123')
  .then(() => {
    console.log('Logged in');
    loadMovies();
  })
  .catch(err => console.error(err.message));

function loadMovies() {
  db.collection('movies').get().then(snapshot => {
    snapshot.docs.forEach(doc => {
      const movie = doc.data();
      const div = document.createElement('div');
      div.className = 'movie';
      div.innerHTML = `<img src="${movie.image}" alt="${movie.title}">`;
      movieList.appendChild(div);
    });
  });
  {
  "title": "Movie 1",
  "image": "https://yourdomain.com/path-to-image.jpg"
}
// script.js

document.addEventListener("DOMContentLoaded", function () { const movieList = document.getElementById("movie-list"); const loginBtn = document.getElementById("login-btn"); const profileBtn = document.createElement("button"); profileBtn.id = "profile-btn"; profileBtn.innerText = "Profile"; document.querySelector("header").appendChild(profileBtn);

const db = firebase.firestore();
const auth = firebase.auth();

function loadMovies(category = "Trending") {
    movieList.innerHTML = "";
    db.collection("movies").where("category", "==", category).get().then(snapshot => {
        snapshot.docs.forEach(doc => {
            const movie = doc.data();
            const div = document.createElement("div");
            div.className = "movie";
            div.innerHTML = `<img src="${movie.image}" alt="${movie.title}">`;
            movieList.appendChild(div);
        });
    });
}

function checkAuth() {
    auth.onAuthStateChanged(user => {
        if (user) {
            loginBtn.style.display = "none";
            profileBtn.style.display = "block";
        } else {
            loginBtn.style.display = "block";
            profileBtn.style.display = "none";
        }
    });
}

loginBtn.addEventListener("click", () => {
    auth.signInWithEmailAndPassword("user@example.com", "password123")
        .then(() => alert("Logged in successfully!"))
        .catch(err => alert(err.message));
});

profileBtn.addEventListener("click", () => {
    window.location.href = "profile.html";
});

checkAuth();
loadMovies();

});

<!DOCTYPE html><html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Profile</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="profile-container">
        <img id="profile-pic" src="assets/default-profile.png" alt="Profile Picture">
        <h2 id="username">User Name</h2>
        <button id="logout-btn">Logout</button>
    </div><script>
    const auth = firebase.auth();
    
    auth.onAuthStateChanged(user => {
        if (user) {
            document.getElementById("username").innerText = user.email;
        } else {
            window.location.href = "index.html";
        }
    });
    
    document.getElementById("logout-btn").addEventListener("click", () => {
        auth.signOut().then(() => {
            window.location.href = "index.html";
        });
    });
</script>

</body>
</html>

}
