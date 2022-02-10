# api-dioshopping
Backend criado durante o Labs na DIO com node e typescript
Validação de email,eu fiz uma pequena função,para que ,quando uma pessoa colocar qualquer informação não passe,só passe um email obrigatório.
Ainda estou aprendendo,então,se houver erro ,pode me corrigir
abaixo o código na parte que incluí a função

import { useState, useEffect } from 'react';
import { Grid, Button, TextField } from '@material-ui/core/';

const Contatos = () => {

    const url = 'http://localhost:5000/message'
    const [message, setMessage] = useState([]);
    const [author, setAuthor] = useState('');
    const [content, setContent] = useState('');
    const [validator, setValidator] = useState(false);
    const [render, setRender] = useState(false);
    const [success, setSuccess] = useState(false);

    useEffect(async () => {
        const response = await fetch(url)
        const data = await response.json();
        setMessage(data);
    }, [render])

    const sendMessage = () => {
        setValidator(false);
        if(author.length <= 0 || content.length <= 0){
            return setValidator(!validator)
        }
       function setValidator(email){
       var re=/\s@+\s+\.\s/;
       return ( re.test (email));
    }

              
        const bodyForm = {
            email: author,
            message: content,
        }
