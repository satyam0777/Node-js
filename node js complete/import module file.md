// 1. Importing the fs module
const fs = require('fs');

// 2. Asynchronous File Reading (Non-blocking)
fs.readFile('test.txt', 'utf8', (err, data) => {
  // 3. Error-First Callback Pattern
  if (err) {
    console.error('Error reading file:', err);
    return;
  }
  // 4. Output file contents if successful
  console.log('File contents:', data);
});

// 5. Synchronous File Reading (Blocking - Not recommended for servers)
try {
  const syncData = fs.readFileSync('test.txt', 'utf8');
  console.log('Sync file contents:', syncData);
} catch (err) {
  console.error('Sync error reading file:', err);
}

// 6. Reading file as Buffer (no encoding)
fs.readFile('test.txt', (err, bufferData) => {
  if (err) {
    console.error('Error reading file as buffer:', err);
    return;
  }
  console.log('Buffer data:', bufferData);
  console.log('Buffer as string:', bufferData.toString('utf8'));
});

// 7. Writing to a file asynchronously
fs.writeFile('output.txt', 'Hello, Node.js!', err => {
  if (err) {
    console.error('Error writing file:', err);
    return;
  }
  console.log('File written successfully!');
});

// 8. Appending to a file asynchronously
fs.appendFile('output.txt', '\nAppended text.', err => {
  if (err) {
    console.error('Error appending to file:', err);
    return;
  }
  console.log('Text appended successfully!');
});

// 9. Deleting a file asynchronously
fs.unlink('output.txt', err => {
  if (err) {
    console.error('Error deleting file:', err);
    return;
  }
  console.log('File deleted successfully!');
});

// 10. Checking if a file exists (synchronously)
if (fs.existsSync('test.txt')) {
  console.log('test.txt exists!');
} else {
  console.log('test.txt does not exist!');
}

// 11. Interview Questions (as comments)
// - How do you read a file asynchronously in Node.js?
// - What is the error-first callback pattern?
// - What happens if you omit the encoding in fs.readFile?
// - How do you handle file read errors?
// - What’s the difference between fs.readFile and fs.readFileSync?
// - How do you write, append, and delete files using fs module?
// - How do you check if a