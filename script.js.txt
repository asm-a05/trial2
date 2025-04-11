document.addEventListener('DOMContentLoaded', () => {
  const input = document.getElementById('taskInput');
  const addBtn = document.getElementById('addBtn');
  const taskList = document.getElementById('taskList');

  function addTask() {
    const taskText = input.value.trim();
    if (taskText === '') return;

    // Create new list item
    const li = document.createElement('li');
    li.textContent = taskText;

    // Mark as done when clicked
    li.addEventListener('click', () => {
      li.classList.toggle('done');
    });

    // Right-click to remove
    li.addEventListener('contextmenu', (e) => {
      e.preventDefault();
      li.remove();
    });

    // Add to the list and clear input
    taskList.appendChild(li);
    input.value = '';
  }

  // Click Add button
  addBtn.addEventListener('click', addTask);

  // Press Enter key
  input.addEventListener('keypress', (e) => {
    if (e.key === 'Enter') {
      addTask();
    }
  });
});
