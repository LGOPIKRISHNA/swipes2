{% load static %}
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>E-Land Records - Clerk Dashboard</title>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&display=swap"
rel="stylesheet" />
<link rel="stylesheet"
href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css"
/>
<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Inter', sans-serif;
}
body {
  background-color: #f5f5f5;
  overflow-x: hidden;
}
/* Header styles */
.header {
  background-color: #4cb4e7;
  color: white;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 20px;
  height: 70px;
}
.logo-container {
  display: flex;
  align-items: center;
}
.logo-container img {
  height: 40px;
  width: 40px;
  margin-right: 10px;
}
.title {
  font-size: 24px;
  font-weight: bold;
}
.header-right {
  font-size: 24px;
  font-weight: bold;
}
/* Top navigation */
.top-nav {
  background-color: #4cb4e7;
  color: white;
  display: flex;
  justify-content: flex-end;
  padding: 5px 20px;
  border-top: 1px solid rgba(255, 255, 255, 0.2);
}
.top-nav-item {
  display: flex;
  align-items: center;
  margin-left: 15px;
  cursor: pointer;
}
.top-nav-item i {
  margin-right: 5px;
}
/* Main layout */
.main-container {
  display: flex;
  height: calc(100vh - 110px);
}
/* Sidebar */
.sidebar {
  width: 180px;
  background-color: #4cb4e7;
  color: white;
  padding-top: 20px;
}
.user-profile {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 20px;
}
.user-avatar {
  width: 80px;
  height: 80px;
  background-color: white;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 10px;
}
.user-avatar i {
  font-size: 40px;
  color: #666;
}
.user-name {
  font-weight: bold;
  margin-bottom: 5px;
}
.sidebar-menu {
  list-style: none;
}
.sidebar-menu li {
  margin-bottom: 2px;
}
.sidebar-menu a {
  display: flex;
  align-items: center;
  padding: 10px 15px;
  color: white;
  text-decoration: none;
  transition: background-color 0.3s;
}
.sidebar-menu a:hover, .sidebar-menu a.active {
  background-color: rgba(255, 255, 255, 0.2);
}
.sidebar-menu i {
  margin-right: 10px;
  width: 20px;
  text-align: center;
}
/* Content area */
.content {
  flex: 1;
  padding: 20px;
  background-color: #f5f5f5;
  overflow: auto;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(2, 1fr);
  gap: 20px;
}
.panel {
  background-color: white;
  border-radius: 5px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  overflow: hidden;
}
.panel-header {
  background-color: #4cb4e7;
  color: white;
  padding: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.panel-title {
  font-weight: bold;
}
.panel-controls {
  display: flex;
  gap: 10px;
}
.panel-controls i {
  cursor: pointer;
}
.panel-content {
  padding: 10px;
  height: calc(100% - 40px);
  overflow: auto;
}
.panel-tabs {
  display: flex;
  border-bottom: 1px solid #ddd;
}
.panel-tab {
  padding: 8px 15px;
  cursor: pointer;
  background-color: #f0f0f0;
  border-right: 1px solid #ddd;
  user-select: none;
}
.panel-tab.active {
  background-color: white;
  border-bottom: 2px solid #4cb4e7;
}
.no-records {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  color: #666;
}

.eland-alerts-content {
padding: 15px;
}
.eland-alerts-container {
background-color: white;
border: 1px solid #ddd;
}
.eland-alert-tabs {
display: flex;
background-color: #f5f5f5;
border-bottom: 1px solid #ddd;
}
.eland-alert-tab {
padding: 8px 15px;
font-size: 14px;
border-right: 1px solid #ddd;
}
.eland-alert-content {
min-height: 200px;
padding: 15px;
}
/* Footer */
.footer {
  background-color: #4cb4e7;
  color: white;
  padding: 10px 20px;
  text-align: center;
  font-size: 12px;
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 10;
}
/* Callout */
.callout {
  position: absolute;
  background-color: #ff7f50;
  color: white;
  padding: 10px 15px;
  border-radius: 5px;
  font-weight: bold;
  z-index: 100;
}
.callout-arrow {
  position: absolute;
  width: 0;
  height: 0;
  border-style: solid;
  z-index: 99;
}
/* Specific panel styles */
#eFile {
  grid-column: 1 / 2;
  grid-row: 1 / 2;
}
#notes {
  grid-column: 2 / 3;
  grid-row: 1 / 2;
}
#team {
  grid-column: 3 / 4;
  grid-row: 1 / 2;
}
#todoList {
  grid-column: 1 / 2;
  grid-row: 2 / 3;
}
#noticeBoard {
  grid-column: 2 / 3;
  grid-row: 2 / 3;
}
/* Connect section */
.connect-section {
  grid-column: 3 / 4;
  grid-row: 2 / 3;
  background-color: #e6f7ff;
  border-radius: 5px;
  overflow: hidden;
}
.connect-header {
  background-color: #4cb4e7;
  color: white;
  padding: 10px;
  font-weight: bold;
}
.connect-list {
  list-style: none;
}
.connect-item {
  padding: 10px;
  border-bottom: 1px solid #ddd;
  display: flex;
  align-items: center;
  cursor: pointer;
  user-select: none;
}
.connect-item i {
  margin-right: 10px;
  color: #4cb4e7;
}

/* Modal styles */
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: none; /* Use flex when visible */
  justify-content: center;
  align-items: center;
  z-index: 1000;
}
.modal-content {
  background-color: white;
  border-radius: 5px;
  width: 500px;
  max-width: 90%;
  max-height: 90%;
  overflow: auto;
  box-shadow: 0 4px 20px rgba(0,0,0,0.3);
}
.modal-header {
  background-color: #4cb4e7;
  color: white;
  padding: 10px 15px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.modal-body {
  padding: 15px;
}
.close-button {
  background: none;
  border: none;
  color: white;
  font-size: 22px;
  cursor: pointer;
  line-height: 1;
}
.modal-input {
  width: 100%;
  padding: 8px 10px;
  margin: 10px 0;
  border-radius: 3px;
  border: 1px solid #aaa;
  font-size: 14px;
}

.panel-tab-content-flex {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

/* Scrollable list styling */
.scroll-list {
  max-height: 240px;
  overflow-y: auto;
  border: 1px solid #ddd;
  border-radius: 3px;
  padding: 10px;
}

/* Buttons */
.button-primary {
  padding: 8px 16px;
  background-color: #4cb4e7;
  color: white;
  border: none;
  border-radius: 3px;
  cursor: pointer;
  font-weight: 600;
}
.button-secondary {
  background-color: #f0f0f0;
  color: #333;
  border: 1px solid #aaa;
}

.button-primary:hover {
  background-color: #3a9adf;
}

.button-secondary:hover {
  background-color: #ddd;
}

/* Form label */
.form-label {
  font-weight: 600;
  margin-bottom: 4px;
  display: block;
}
</style>
<script>
/* ----------- Helper Functions ----------- */
function showModal(modalId) {
  document.getElementById(modalId).style.display = 'flex';
}
function closeModal(modalId) {
  document.getElementById(modalId).style.display = 'none';
}

/* ----------- VC Room Functionality ----------- */
function generateRoomId() {
  return 'vc-' + Math.random().toString(36).substr(2, 9);
}
function getRoomUrl(roomId) {
  return window.location.origin + "/vc-room/?room=" + roomId;
}
function openVcRoomModal() {
  const roomId = generateRoomId();
  const roomUrl = getRoomUrl(roomId);
  const vcRoomSection = document.getElementById("vcRoomSection");
  vcRoomSection.innerHTML = `
    <div style="margin-bottom:16px;">
      <div><strong>Your VC Room Link (share with others to join):</strong></div>
      <input type="text" value="${roomUrl}" id="currentRoomLink" readonly style="width:80%;padding:6px;border-radius:3px;border:1px solid #aaa;" />
      <button onclick="copyToClipboard('currentRoomLink')" style="margin-left:8px;padding:4px 10px;">Copy</button>
      <div style="margin-top:16px;">
        <button onclick="window.open('${roomUrl}', '_blank')" class="button-primary">Enter VC Room</button>
      </div>
    </div>
    <hr />
    <div>
      <div style="font-weight:bold;">Join a VC Room:</div>
      <input type="text" id="joinRoomLink" placeholder="Paste room link" class="modal-input" />
      <button onclick="joinVcRoom()" class="button-primary">Join</button>
    </div>
  `;
  showModal('vcRoomModal');
}
function closeVcRoomModal() {
  closeModal('vcRoomModal');
}
function copyToClipboard(inputId) {
  const input = document.getElementById(inputId);
  input.select();
  input.setSelectionRange(0, 99999); // For mobile devices
  document.execCommand("copy");
  alert("Copied link!");
}
function joinVcRoom() {
  const link = document.getElementById('joinRoomLink').value;
  if (link) {
    window.open(link, '_blank');
  } else {
    alert("Please paste a valid VC Room link!");
  }
}

/* -------- Connect Section: Other Modals -------- */
function openDirectory() {
  const title = document.getElementById("connectModalTitle");
  const icon = document.getElementById("connectModalIcon");
  const body = document.getElementById("connectModalBody");
  title.textContent = " Directory";
  icon.className = "fas fa-address-book";
  body.innerHTML = `
    <p>This is the Directory where you can find contacts of departments and key officials.</p>
    <p><em>(Feature to be implemented)</em></p>
  `;
  showModal("connectModal");
}

function openQuickConnect() {
  const title = document.getElementById("connectModalTitle");
  const icon = document.getElementById("connectModalIcon");
  const body = document.getElementById("connectModalBody");
  title.textContent = " Quick Connect";
  icon.className = "fas fa-bolt";
  body.innerHTML = `
    <p>Quick Connect lets you instantly contact team members or officials.</p>
    <p><em>(Feature to be implemented)</em></p>
  `;
  showModal("connectModal");
}

function openEvents() {
  const title = document.getElementById("connectModalTitle");
  const icon = document.getElementById("connectModalIcon");
  const body = document.getElementById("connectModalBody");
  title.textContent = " Events";
  icon.className = "fas fa-calendar-alt";
  body.innerHTML = `
    <p>View upcoming events and important dates related to land records and administration.</p>
    <p><em>(Feature to be implemented)</em></p>
  `;
  showModal("connectModal");
}

function openContactsGroup() {
  const title = document.getElementById("connectModalTitle");
  const icon = document.getElementById("connectModalIcon");
  const body = document.getElementById("connectModalBody");
  title.textContent = " My Contacts/Group";
  icon.className = "fas fa-users";
  body.innerHTML = `
    <p>Manage your personal contacts and groups.</p>
    <p><em>(Feature to be implemented)</em></p>
  `;
  showModal("connectModal");
}

/* -------- Notice Board Functionality -------- */
document.addEventListener("DOMContentLoaded", () => {
  // Simple notice board data example
  const notices = [
    { id: 1, title: "Land Registration Deadline", content: "Submit all pending land registration documents by July 31." },
    { id: 2, title: "System Maintenance", content: "The system will be down on Aug 5 from 12 AM to 4 AM." }
  ];
  const centralDocs = [
    { id: 1, name: "Land Ownership Act.pdf" },
    { id: 2, name: "Property Transfer Rules.docx" }
  ];
  const myDocs = [
    { id: 1, name: "My Application Summary.pdf" }
  ];

function showNotifications() {
// Create and show notifications panel
const modal = document.createElement("div");
modal.className = "modal";
modal.innerHTML = `
<div class="modal-content">
<div class="modal-header">
<h2><i class="fas fa-bell"></i> Notifications</h2>
<button class="close-button"
onclick="this.closest('.modal').remove()">×</button>
</div>
<div class="modal-body">
<div class="notifications-panel">
<div class="notification-list">
<div class="notification-item">
<i class="fas fa-file-alt"></i>
<div class="notification-content">
<div class="notification-title">New Application Received</div>
<div class="notification-time">2 minutes ago</div>
</div>
</div>
<div class="notification-item">
<i class="fas fa-check-circle"></i>
<div class="notification-content">
<div class="notification-title">Document Verification Required</div>
<div class="notification-time">1 hour ago</div>
</div>
</div>
<!-- Add more notification items as needed -->
</div>
</div>
</div>
</div>
`;
document.body.appendChild(modal);
}

function showTasks() {
// Create and show tasks panel
const modal = document.createElement("div");
modal.className = "modal";
modal.innerHTML = `
<div class="modal-content">
<div class="modal-header">
<h2><i class="fas fa-tasks"></i> Tasks</h2>
<button class="close-button"
onclick="this.closest('.modal').remove()">×</button>
</div>
<div class="modal-body">
<div class="task-list">
<div class="task-item">
<input type="checkbox" id="task1">
<label for="task1">Review pending applications</label>
<span class="task-date">Today</span>
</div>
<div class="task-item">
<input type="checkbox" id="task2">
<label for="task2">Verify submitted documents</label>
<span class="task-date">Today</span>
</div>
<div class="task-item">
<input type="checkbox" id="task3">
<label for="task3">Generate monthly report</label>
<span class="task-date">Tomorrow</span>
</div>
<!-- Add more task items as needed -->
</div>
</div>
</div>
`;
document.body.appendChild(modal);
}

function showProfile() {
// Create and show profile panel
const modal = document.createElement("div");
modal.className = "modal";
modal.innerHTML = `
<div class="modal-content">
<div class="modal-header">
<h2><i class="fas fa-user"></i> Profile</h2>
<button class="close-button"
onclick="this.closest('.modal').remove()">×</button>
</div>
<div class="modal-body">
<div class="profile-panel">
<div class="profile-content">
<div class="profile-info">
<div class="profile-avatar">
<i class="fas fa-user-tie"></i>
</div>
<h4>Clerk Name</h4>
<p>IDTA Office</p>
</div>
<div class="profile-details">
<div class="detail-item">
<label>Employee ID</label>
<input type="text" value="CLK001" readonly>
</div>
<div class="detail-item">
<label>Email</label>
<input type="email" value="clerk@idta.gov.in" class="editable">
</div>
<div class="detail-item">
<label>Phone</label>
<input type="tel" value="+91 9876543210" class="editable">
</div>
<div class="detail-item">
<label>Department</label>
<input type="text" value="Land Records" readonly>
</div>
</div>
<button class="edit-profile-button">
<i class="fas fa-edit"></i> Edit Profile
</button>
</div>
</div>
</div>
</div>
`;
document.body.appendChild(modal);

  function renderNoticeBoardTab() {
    const container = document.getElementById("noticeBoardContent");
    if (!container) return;
    let html = `<div class="scroll-list">`;
    if (notices.length === 0) {
      html += "<p>No notices available.</p>";
    } else {
      notices.forEach(n => {
        html += `<div><strong>${n.title}</strong><br/><small>${n.content}</small><hr/></div>`;
      });
    }
    html += "</div>";
    container.innerHTML = html;
  }
  function renderCentralDocsTab() {
    const container = document.getElementById("centralDocsContent");
    if (!container) return;
    let html = `<div class="scroll-list">`;
    if (centralDocs.length === 0) {
      html += "<p>No central documents found.</p>";
    } else {
      centralDocs.forEach(doc => {
        html += `<div><i class="fas fa-file-alt" style="color:#4cb4e7;"></i> ${doc.name}</div>`;
      });
    }
    html += "</div>";
    container.innerHTML = html;
  }
  function renderMyDocsTab() {
    const container = document.getElementById("myDocsContent");
    if (!container) return;
    let html = `<div class="scroll-list">`;
    if (myDocs.length === 0) {
      html += "<p>No personal documents found.</p>";
    } else {
      myDocs.forEach(doc => {
        html += `<div><i class="fas fa-file-alt" style="color:#4cb4e7;"></i> ${doc.name}</div>`;
      });
    }
    html += "</div>";
    container.innerHTML = html;
  }

  // Initially render all tabs but show only Notice Board tab content
  renderNoticeBoardTab();
  renderCentralDocsTab();
  renderMyDocsTab();

  // Setup tab switching
  document.querySelectorAll("#noticeBoard .panel-tab").forEach(tab => {
    tab.addEventListener("click", () => {
      // Remove active class on all tabs
      document.querySelectorAll("#noticeBoard .panel-tab").forEach(t => t.classList.remove("active"));
      tab.classList.add("active");

      // Show/hide content divs based on tab text
      const tabText = tab.textContent.trim();
      document.getElementById("noticeBoardContent").style.display = tabText === "Notice Board" ? "block" : "none";
      document.getElementById("centralDocsContent").style.display = tabText === "Central Docs" ? "block" : "none";
      document.getElementById("myDocsContent").style.display = tabText === "My Docs" ? "block" : "none";
    });
  });
});

/* -------- To Do List Functionality -------- */
const todoList = [];
function renderTodoList() {
  const container = document.getElementById("todoListContent");
  if (!container) return;
  if (todoList.length === 0) {
    container.innerHTML = `<p>No To Do items found.</p>`;
    return;
  }
  let html = `<ul style="list-style:none; padding-left:0;">`;
  todoList.forEach((todo, index) => {
    html += `
      <li style="margin-bottom:8px; display:flex; align-items:center; justify-content:space-between;">
        <label>
          <input type="checkbox" onchange="toggleTodoComplete(${index}, this.checked)" ${todo.completed ? "checked" : ""}>
          <span style="margin-left:10px;${todo.completed ? "text-decoration: line-through; color:#666;" : ""}">
            ${todo.text}
          </span>
        </label>
        <button onclick="removeTodo(${index})" style="color: red; border:none; background:none; cursor:pointer;" title="Remove">&times;</button>
      </li>`;
  });
  html += `</ul>`;
  container.innerHTML = html;
}

function addTodoItem() {
  const input = document.getElementById("newTodoInput");
  const val = input.value.trim();
  if (val === "") {
    alert("Please enter a valid to do item.");
    return;
  }
  todoList.push({ text: val, completed: false });
  input.value = "";
  renderTodoList();
}

function toggleTodoComplete(index, completed) {
  todoList[index].completed = completed;
  renderTodoList();
}

function removeTodo(index) {
  if (confirm("Are you sure to delete this to do item?")) {
    todoList.splice(index, 1);
    renderTodoList();
  }
}

function openTodoModal() {
  renderTodoList();
  showModal("todoModal");
}
function closeTodoModal() {
  closeModal("todoModal");
}

/* -------- Team Section Functionality -------- */
const teamMembers = [];
function renderTeamMembers() {
  const container = document.getElementById("teamListContent");
  if (!container) return;
  if (teamMembers.length === 0) {
    container.innerHTML = `<p>No team members added.</p>`;
    return;
  }
  let html = `<ul style="list-style:none; padding-left:0;">`;
  teamMembers.forEach((member, index) => {
    html += `
      <li style="margin-bottom:8px; display:flex; justify-content:space-between; align-items:center;">
        <span>${member}</span>
        <button onclick="removeTeamMember(${index})" style="color: red; border:none; background:none; cursor:pointer;" title="Remove">&times;</button>
      </li>`;
  });
  html += `</ul>`;
  container.innerHTML = html;
}
function addTeamMember() {
  const input = document.getElementById("newTeamMemberInput");
  const val = input.value.trim();
  if (val === "") {
    alert("Please enter a valid team member name.");
    return;
  }
  teamMembers.push(val);
  input.value = "";
  renderTeamMembers();
}
function removeTeamMember(index) {
  if (confirm("Are you sure to remove this member?")) {
    teamMembers.splice(index, 1);
    renderTeamMembers();
  }
}
function openTeamModal() {
  renderTeamMembers();
  showModal("teamModal");
}
function closeTeamModal() {
  closeModal("teamModal");
}

/* -------- Notes Section Functionality -------- */
const notes = [];
function renderNotesList() {
  const container = document.getElementById("notesListContent");
  if (!container) return;
  if (notes.length === 0) {
    container.innerHTML = `<p>No notes available.</p>`;
    return;
  }
  let html = `<ul style="list-style:none; padding-left:0;">`;
  notes.forEach((note, index) => {
    html += `
      <li style="margin-bottom:10px;">
        <div style="display: flex; justify-content: space-between; align-items: center;">
          <strong>Note ${index+1}</strong>
          <button onclick="removeNote(${index})" style="color:red; border:none; background:none; cursor:pointer;" title="Remove">&times;</button>
        </div>
        <p style="white-space: pre-wrap; background: #f9f9f9; padding: 8px; border-radius: 3px; border: 1px solid #ddd;">${note}</p>
      </li>`;
  });
  html += "</ul>";
  container.innerHTML = html;
}
function addNote() {
  const input = document.getElementById("newNoteTextarea");
  const val = input.value.trim();
  if(val === "") {
    alert("Please enter note content");
    return;
  }
  notes.push(val);
  input.value = "";
  renderNotesList();
}
function removeNote(index) {
  if (confirm("Are you sure to delete this note?")) {
    notes.splice(index, 1);
    renderNotesList();
  }
}
function openNotesModal() {
  renderNotesList();
  showModal("notesModal");
}
function closeNotesModal() {
  closeModal("notesModal");
}

/* ----------------- Connect Section Clicks ----------------- */
document.addEventListener('DOMContentLoaded', function() {
  const vcRoomLink = document.getElementById('vcRoomLink');
  if (vcRoomLink) {
    vcRoomLink.addEventListener('click', function(e) {
      e.preventDefault();
      openVcRoomModal();
    });
  }

  // Assuming Directory, Quick Connect, Events, My Contacts/Group had no IDs, assign events using index to match UI
  // Better to add IDs, but given code, let's add minimal listeners here:
  const connectItems = document.querySelectorAll(".connect-section .connect-list .connect-item");
  connectItems.forEach((elem) => {
    const text = elem.querySelector("span").textContent.trim();
    switch(text) {
      case "Directory":
        elem.addEventListener("click", function(e){
          e.preventDefault();
          openDirectory();
        });
        break;
      case "Quick Connect":
        elem.addEventListener("click", function(e){
          e.preventDefault();
          openQuickConnect();
        });
        break;
      case "Events":
        elem.addEventListener("click", function(e){
          e.preventDefault();
          openEvents();
        });
        break;
      case "My Contacts/Group":
        elem.addEventListener("click", function(e){
          e.preventDefault();
          openContactsGroup();
        });
        break;
    }
  });

  // Notice Board Panel Tabs functionality is initialized in above script block in DOMContentLoaded
});

/* ---------------- Additional existing functions for profile, notifications, tasks, logout etc. from your current code here ---------------- */

function showNotifications() {
  const modal = document.createElement("div");
  modal.className = "modal";
  modal.innerHTML = `
    <div class="modal-content">
      <div class="modal-header">
        <h2><i class="fas fa-bell"></i> Notifications</h2>
        <button class="close-button" onclick="this.closest('.modal').remove()">×</button>
      </div>
      <div class="modal-body">
        <div class="notifications-panel">
          <div class="notification-list">
            <div class="notification-item">
              <i class="fas fa-file-alt"></i>
              <div class="notification-content">
                <div class="notification-title">New Application Received</div>
                <div class="notification-time">2 minutes ago</div>
              </div>
            </div>
            <div class="notification-item">
              <i class="fas fa-check-circle"></i>
              <div class="notification-content">
                <div class="notification-title">Document Verification Required</div>
                <div class="notification-time">1 hour ago</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  `;
  document.body.appendChild(modal);
}

function showProfile() {
  const modal = document.createElement("div");
  modal.className = "modal";
  modal.innerHTML = `
    <div class="modal-content">
      <div class="modal-header">
        <h2><i class="fas fa-user"></i> Profile</h2>
        <button class="close-button"
          onclick="this.closest('.modal').remove()">×</button>
      </div>
      <div class="modal-body">
        <div class="profile-panel">
          <div class="profile-content">
            <div class="profile-info">
              <div class="profile-avatar">
                <i class="fas fa-user-tie"></i>
              </div>
              <h4>Clerk Name</h4>
              <p>IDTA Office</p>
            </div>
            <div class="profile-details">
              <div class="detail-item">
                <label>Employee ID</label>
                <input type="text" value="CLK001" readonly>
              </div>
              <div class="detail-item">
                <label>Email</label>
                <input type="email" value="clerk@idta.gov.in" class="editable">
              </div>
              <div class="detail-item">
                <label>Phone</label>
                <input type="tel" value="+91 9876543210" class="editable">
              </div>
              <div class="detail-item">
                <label>Department</label>
                <input type="text" value="Land Records" readonly>
              </div>
            </div>
            <button class="edit-profile-button button-primary">
              <i class="fas fa-edit"></i> Edit Profile
            </button>
          </div>
        </div>
      </div>
    </div>
  `;
  document.body.appendChild(modal);
  const editButton = modal.querySelector(".edit-profile-button");
  const editableInputs = modal.querySelectorAll(".editable");
  editButton.addEventListener("click", function () {
    if (this.textContent.includes("Edit")) {
      editableInputs.forEach((input) =>
        input.removeAttribute("readonly")
      );
      this.innerHTML = '<i class="fas fa-save"></i> Save Changes';
    } else {
      editableInputs.forEach((input) =>
        input.setAttribute("readonly", true)
      );
      this.innerHTML = '<i class="fas fa-edit"></i> Edit Profile';
      alert("Profile changes saved successfully!");
    }
  });
}

function showTasks() {
  const modal = document.createElement("div");
  modal.className = "modal";
  modal.innerHTML = `
  <div class="modal-content">
    <div class="modal-header">
      <h2><i class="fas fa-tasks"></i> Tasks</h2>
      <button class="close-button" onclick="this.closest('.modal').remove()">×</button>
    </div>
    <div class="modal-body">
      <div class="task-list">
        <div class="task-item">
          <input type="checkbox" id="task1">
          <label for="task1">Review pending applications</label>
          <span class="task-date">Today</span>
        </div>
        <div class="task-item">
          <input type="checkbox" id="task2">
          <label for="task2">Verify submitted documents</label>
          <span class="task-date">Today</span>
        </div>
        <div class="task-item">
          <input type="checkbox" id="task3">
          <label for="task3">Generate monthly report</label>
          <span class="task-date">Tomorrow</span>
        </div>
      </div>
    </div>
  </div>
  `;
  document.body.appendChild(modal);
}

function handleLogout() {
  if (confirm("Are you sure you want to logout?")) {
    window.location.href = "index.html";
  }
}

</script>
</head>
<body>
<!-- Header -->
<div class="header">
  <div class="logo-container">
    <img src="{% static 'img/earth.png' %}" alt="Logo" />
    <span class="title">E - Land Records</span>
  </div>
  <div class="header-right">
    Land Record Management
  </div>
</div>

<!-- Top Navigation -->
<div class="top-nav">
<div class="top-nav-item" onclick="showProfile()">
<i class="fas fa-user-circle"></i>
<span>Set Status</span>
</div>
<div class="top-nav-item" onclick="showNotifications()">
<i class="fas fa-bell"></i>
<span>Alerts</span>
</div>
<div class="top-nav-item" onclick="showProfile()">
<i class="fas fa-cog"></i>
<span>Settings</span>
</div>
<div class="top-nav-item" onclick="handleLogout()">
<i class="fas fa-sign-out-alt"></i>
<span>Logout</span>
</div>
</div>


<!-- Main Container -->
<div class="main-container">
  <!-- Sidebar -->
  <div class="sidebar">
    <div class="user-profile">
      <div class="user-avatar">
        <i class="fas fa-user"></i>
      </div>
      <div class="user-name">{{user.designation}}</div>
      <div class="user-role">{{user.get_full_name}}</div>
    </div>
    <ul class="sidebar-menu">
      <li>
        <a href="#" class="active">
          <i class="fas fa-home"></i>
          <span>Home</span>
        </a>
      </li>
      <li>
        <a href="{% url 'official_eLand' %}">
          <i class="fas fa-file-alt"></i>
          <span>eLand</span>
        </a>
      </li>
      <li>
        <a href="#">
          <i class="fas fa-tasks"></i>
          <span>Track Application</span>
        </a>
      </li>
      <li>
        <a href="#">
          <i class="fas fa-envelope"></i>
          <span>Mail</span>
        </a>
      </li>
      <li>
        <a href="#">
          <i class="fas fa-cogs"></i>
          <span>Other Services</span>
        </a>
      </li>
      <li>
        <a href="#" onclick="openTeamModal(); return false;">
          <i class="fas fa-clipboard-list"></i>
          <span>Tasks</span>
        </a>
      </li>
      <li>
        <a href="#" onclick="openTodoModal(); return false;">
          <i class="fas fa-check-square"></i>
          <span>To do list</span>
        </a>
      </li>
      <li>
        <a href="#" onclick="openNotesModal(); return false;">
          <i class="fas fa-sticky-note"></i>
          <span>Notes</span>
        </a>
      </li>
      <li>
        <a href="#">
          <i class="fas fa-download"></i>
          <span>Download Forms</span>
        </a>
      </li>
    </ul>
  </div>

  <!-- Content Area -->
  <div class="content">
    <!-- eFile Panel -->
    <div id="eFile" class="panel">
      <div class="panel-header">
        <div class="panel-title">
          <i class="fas fa-file-alt"></i> eFile
        </div>
        <div class="panel-controls">
          <i class="fas fa-search"></i>
          <i class="fas fa-sync-alt"></i>
          <i class="fas fa-question-circle"></i>
        </div>
      </div>
      <div class="panel-content">
        <div class="panel-tabs">
          <div class="panel-tab active">eFile</div>
          <div class="panel-tab">Receipts</div>
        </div>
        <div class="no-records">
          <p>No record found.</p>
        </div>
      </div>
    </div>

    <!-- Notes Panel (summary removed, use modal) -->
    <div id="notes" class="panel">
      <div class="panel-header">
        <div class="panel-title">
          <i class="fas fa-sticky-note"></i> Notes
        </div>
        <div class="panel-controls">
          <i class="fas fa-search"></i>
          <i class="fas fa-plus" onclick="openNotesModal()" style="cursor:pointer;"></i>
          <i class="fas fa-sync-alt"></i>
          <i class="fas fa-question-circle"></i>
        </div>
      </div>
      <div class="panel-content">
        <p>Use the Notes menu in the sidebar to manage notes.</p>
      </div>
    </div>

    <!-- Team Panel -->
    <div id="team" class="panel">
      <div class="panel-header">
        <div class="panel-title">
          <i class="fas fa-users"></i> Team
        </div>
        <div class="panel-controls">
          <i class="fas fa-search"></i>
          <i class="fas fa-sync-alt"></i>
          <i class="fas fa-question-circle"></i>
          <i class="fas fa-plus" onclick="openTeamModal()" style="cursor:pointer;"></i>
        </div>
      </div>
      <div class="panel-content">
        <p>Use the Tasks menu in the sidebar to manage your team.</p>
      </div>
    </div>

    <!-- To Do List Panel -->
    <div id="todoList" class="panel">
      <div class="panel-header">
        <div class="panel-title">
          <i class="fas fa-check-square"></i> To Do List
        </div>
        <div class="panel-controls">
          <i class="fas fa-plus" onclick="openTodoModal()" style="cursor:pointer;"></i>
          <i class="fas fa-sync-alt"></i>
          <i class="fas fa-question-circle"></i>
        </div>
      </div>
      <div class="panel-content">
        <p>Use the To Do list menu in the sidebar to manage tasks.</p>
      </div>
    </div>

    <!-- Notice Board Panel -->
    <div id="noticeBoard" class="panel">
      <div class="panel-header">
        <div class="panel-title">
          <i class="fas fa-bullhorn"></i> Notice Board
        </div>
        <div class="panel-controls">
          <i class="fas fa-sync-alt"></i>
          <i class="fas fa-question-circle"></i>
          <i class="fas fa-ellipsis-v"></i>
        </div>
      </div>
      <div class="panel-content">
        <div class="panel-tabs">
          <div class="panel-tab active">Notice Board</div>
          <div class="panel-tab">Central Docs</div>
          <div class="panel-tab">My Docs</div>
        </div>
        <div id="noticeBoardContent" style="display:block; margin-top:10px;"></div>
        <div id="centralDocsContent" style="display:none; margin-top:10px;"></div>
        <div id="myDocsContent" style="display:none; margin-top:10px;"></div>
      </div>
    </div>

    <!-- Connect Section -->
    <div class="connect-section">
      <div class="connect-header">Connect</div>
      <ul class="connect-list" style="padding-left:0; margin:0;">
        <li class="connect-item" style="cursor:pointer;">
          <i class="fas fa-address-book"></i>
          <span>Directory</span>
        </li>
        <li class="connect-item" id="vcRoomLink">
          <i class="fas fa-video"></i>
          <span>VC Room</span>
        </li>
        <li class="connect-item" style="cursor:pointer;">
          <i class="fas fa-bolt"></i>
          <span>Quick Connect</span>
        </li>
        <li class="connect-item" style="cursor:pointer;">
          <i class="fas fa-calendar-alt"></i>
          <span>Events</span>
        </li>
        <li class="connect-item" style="cursor:pointer;">
          <i class="fas fa-users"></i>
          <span>My Contacts/Group</span>
        </li>
      </ul>
    </div>
  </div>
</div>

<!-- Modals -->

<!-- VC Room Modal -->
<div id="vcRoomModal" class="modal" >
  <div class="modal-content">
    <div class="modal-header">
      <h2><i class="fas fa-video"></i> VC Room</h2>
      <button class="close-button" onclick="closeVcRoomModal()">×</button>
    </div>
    <div class="modal-body" id="vcRoomSection" style="text-align:center;">
      <!-- Populated dynamically -->
    </div>
  </div>
</div>

<!-- Connect Generic Modal -->
<div id="connectModal" class="modal">
  <div class="modal-content">
    <div class="modal-header">
      <h2><i id="connectModalIcon" class="fas"></i> <span id="connectModalTitle"></span></h2>
      <button class="close-button" onclick="closeModal('connectModal')">×</button>
    </div>
    <div class="modal-body" id="connectModalBody" style="text-align:center;">
      <!-- Populated dynamically -->
    </div>
  </div>
</div>

<!-- To Do List Modal -->
<div id="todoModal" class="modal">
  <div class="modal-content">
    <div class="modal-header">
      <h2><i class="fas fa-check-square"></i> To Do List</h2>
      <button class="close-button" onclick="closeTodoModal()">×</button>
    </div>
    <div class="modal-body">
      <div style="margin-bottom: 10px;">
        <input type="text" id="newTodoInput" placeholder="New To Do Item" class="modal-input" />
        <button onclick="addTodoItem()" class="button-primary" style="margin-top:5px;">Add</button>
      </div>
      <div id="todoListContent"></div>
    </div>
  </div>
</div>

<!-- Team Modal -->
<div id="teamModal" class="modal">
  <div class="modal-content">
    <div class="modal-header">
      <h2><i class="fas fa-users"></i> Team Members</h2>
      <button class="close-button" onclick="closeTeamModal()">×</button>
    </div>
    <div class="modal-body">
      <div style="margin-bottom: 10px;">
        <input type="text" id="newTeamMemberInput" placeholder="Add new team member" class="modal-input" />
        <button onclick="addTeamMember()" class="button-primary" style="margin-top:5px;">Add</button>
      </div>
      <div id="teamListContent"></div>
    </div>
  </div>
</div>

<!-- Notes Modal -->
<div id="notesModal" class="modal">
  <div class="modal-content">
    <div class="modal-header">
      <h2><i class="fas fa-sticky-note"></i> Notes</h2>
      <button class="close-button" onclick="closeNotesModal()">×</button>
    </div>
    <div class="modal-body">
      <textarea id="newNoteTextarea" placeholder="Write a new note..." class="modal-input" rows="4"></textarea>
      <button onclick="addNote()" class="button-primary" style="margin-top:8px;">Add Note</button>
      <div id="notesListContent" style="margin-top:15px;"></div>
    </div>
  </div>
</div>

<!-- Footer -->
<div class="footer">
  Design &amp; developed by National Institute of Technology @ 2025 | Disclaimer | Terms &amp; Conditions | Version
</div>
</body>
</html>
