# Irina Levkovich
***

## CONTACTS
***

+ [GitHub](https://github.com/Iri-iri)
+ [Telegram](https://t.me/HelloSpring_i)
+ [Mail](6346390@mail.ru)

## ABOUT ME
***

I'm 31 years old and I'm a beginning Front-end Developer from Minsk. I was started my education in IT-sphere in May 2020. Besides studying on my own I am also taking courses on frontend development in the coding school TeachMeSkills. I learn quickly, capable of getting a grip of new technologies and picking up on new skills. I'm firm of purpose, responsible and inquisitive. My goal is to get a job or to become a trainee at EPAM as Junior Front-end Developer.

## SKILLS
***

+ HTML & CSS
+ JavaScript
+ Git

## CODE EXAMPLE
***

Code example simple todoList:

    const title = document.querySelector("#title");
    const description = document.querySelector("#description");
    const display = document.querySelector("#display");
    const btn = document.querySelector("#btn");
    const modalWrapper = document.querySelector(".modal-wrapper");
    const closeBtn = document.querySelector("#closeBtn");
    const okBtn = document.querySelector("#okBtn");
    const mess = document.querySelector("#mess");
    const inputTitle = document.querySelector("#new_title");
    const inputDescription = document.querySelector("#new_description");
    const form = document.querySelector("#form");

      let arr = [];

      function displayDate() {
        const myDate = new Date();
        dateValue = `Date:${myDate.getDate()}.0${myDate.getMonth() + 1}.${myDate.getFullYear()}
        Time:${myDate.getHours()}:${myDate.getMinutes()}:${myDate.getSeconds()}`;
        return dateValue;
      }
      function ArrPush() {
        let obj = {
          titleDisplay: title.value,
          descriptionDisplay: description.value,
          date: dateValue,
        };
        arr.push(obj);
      }
      function displayMessage() {
        let displayMessage = "";
        arr.forEach(function (item) {
          displayMessage += `
        <li class = "li">
        <h3 class = "newTitle">${item.titleDisplay}</h3>
        <p class = "newDescription">${item.descriptionDisplay}</p>
        <p>${item.date}</p>
        <button class = "editButton"> Edit </button>
        <button class = "deleteButton"> Delete </button>
        </li>
        `;
      display.innerHTML = displayMessage;
    });
    };

    function openModal() {
      modalWrapper.style.display = "block";
      }
      closeBtn.addEventListener("click", function () {
        modalWrapper.style.display = "none";
      });
      btn.addEventListener("click", (event) => {
      event.preventDefault();
      displayDate();
      ArrPush();
      displayMessage();

      const arrOfLi = document.querySelectorAll(".li");
      arrOfLi.forEach((item) => {
        item.addEventListener("mouseenter", () => {
          item.style.boxShadow = "0 0 3px 5px purple";
        });
        item.addEventListener("mouseleave", () => {
          item.style.boxShadow = "none";
        });
      })
      });

    function del() {
      const newLi = event.target.closest(".li");
      const newTitle = newLi.querySelector(".newTitle").textContent;
      const newDescription = newLi.querySelector(".newDescription").textContent;

      arr.forEach(function (item, index) {
        if (newTitle === item.titleDisplay && newDescription === item.descriptionDisplay) {
          arr.splice(index, 1);
        }
        displayMessage();
      });
    };

    function edit() {
      const newLi = event.target.closest(".li");
      const newTitle = newLi.querySelector(".newTitle").textContent;
      const newDescription = newLi.querySelector(".newDescription").textContent;


      openModal();
      inputTitle.value = `${newTitle}`;
      inputDescription.value = `${newDescription}`;


      okBtn.addEventListener("click", () => {

    arr.forEach(function (item, index) {
      if (newTitle === item.titleDisplay && newDescription === item.descriptionDisplay) {
        displayDate();
        arr.splice(index, 1, {
          titleDisplay: inputTitle.value,
          descriptionDisplay: inputDescription.value,
          date: dateValue,
        });
        modalWrapper.style.display = "none";
      }
      displayMessage();

    });

    });
    }
    
    container.addEventListener("click", (event) => {

      if (event.target.closest(".deleteButton")) {
        del();
      }

      if (event.target.closest(".editButton")) {
        event.preventDefault()
        edit();
      }
    });


