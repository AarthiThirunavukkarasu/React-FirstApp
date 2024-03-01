# React-FirstApp
import React, { useState } from 'react';
import { Container, TextField, Button, Grid, Typography, Card, CardContent } from '@material-ui/core';
import { makeStyles } from '@material-ui/core/styles';

const useStyles = makeStyles((theme) => ({
  container: {
    paddingTop: theme.spacing(4),
    paddingBottom: theme.spacing(4),
    paddingLeft: theme.spacing(2),
    paddingRight: theme.spacing(2),
  },
  messageCard: {
    backgroundColor: '#E5DDD5', // iPhone message app background color
    marginBottom: theme.spacing(1),
    padding: theme.spacing(1),
    borderRadius: 8,
  },
  inputField: {
    backgroundColor: '#F2F2F2', // iPhone message input field background color
    borderRadius: 20,
  },
}));

function MessageSimulator() {
  const classes = useStyles();
  const [messages, setMessages] = useState([]);
  const [inputValue, setInputValue] = useState('');

  const handleMessageSend = () => {
    if (inputValue.trim() !== '') {
      setMessages([...messages, { id: messages.length, text: inputValue }]);
      setInputValue('');
    }
  };

  return (
    <Container maxWidth="sm" className={classes.container}>
      <Typography variant="h4" gutterBottom>
        Messages
      </Typography>
      <Grid container spacing={1}>
        <Grid item xs={12}>
          {messages.map(message => (
            <Card key={message.id} className={classes.messageCard}>
              <CardContent>
                <Typography>{message.text}</Typography>
              </CardContent>
            </Card>
          ))}
        </Grid>
        <Grid item xs={8}>
          <TextField
            fullWidth
            variant="outlined"
            className={classes.inputField}
            placeholder="iMessage"
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
