
import React, { useState } from 'react';
import { Container, TextField, Button, Grid, Typography, Card, CardContent } from '@material-ui/core';

function MessageSimulator() {
  const [messages, setMessages] = useState([]);
  const [inputValue, setInputValue] = useState('');

  const handleMessageSend = () => {
    if (inputValue.trim() !== '') {
      setMessages([...messages, { id: messages.length, text: inputValue }]);
      setInputValue('');
    }
  };

  return (
    <Container maxWidth="sm">
      <Typography variant="h4" gutterBottom>
        Mobile Message Simulator
      </Typography>
      <Grid container spacing={2}>
        <Grid item xs={12}>
          <Card>
            <CardContent>
              {messages.map(message => (
                <Typography key={message.id}>{message.text}</Typography>
              ))}
            </CardContent>
          </Card>
        </Grid>
        <Grid item xs={8}>
          <TextField
            fullWidth
            label="Type your message"
            value={inputValue}
            onChange={(e) => setInputValue(e.target.value)}
          />
        </Grid>
        <Grid item xs={4}>
          <Button variant="contained" color="primary" onClick={handleMessageSend}>
            Send
          </Button>
        </Grid>
      </Grid>
    </Container>
  );
}

export default MessageSimulator;
