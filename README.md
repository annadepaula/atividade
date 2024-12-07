jsx
import React, { useState, useEffect } from 'react';
import { View, Text, FlatList, TouchableOpacity } from 'react-native';

const App = () => {
 const [lembretes, setLembretes] = useState([]);
 const [novoLembrete, setNovoLembrete] = useState('');

 useEffect(() => {
 const lembretesArmazenados = localStorage.getItem('lembretes');
 if (lembretesArmazenados) {
 setLembretes(JSON.parse(lembretesArmazenados));
 }
 }, []);

 const adicionarLembrete = () => {
 const novoLembreteObj = { id: Date.now(), texto: novoLembrete, concluido: false };
 setLembretes([...lembretes, novoLembreteObj]);
 localStorage.setItem('lembretes', JSON.stringify([...lembretes, novoLembreteObj]));
 setNovoLembrete('');
 };

 const marcarConcluido = (id) => {
 const lembretesAtualizados = lembretes.map((lembrete) => {
 if ((link unavailable) === id) {
 return { ...lembrete, concluido: true };
 }
 return lembrete;
 });
 setLembretes(lembretesAtualizados);
 localStorage.setItem('lembretes', JSON.stringify(lembretesAtualizados));
 };

 const excluirLembrete = (id) => {
 const lembretesAtualizados = lembretes.filter((lembrete) => (link unavailable) !== id);
 setLembretes(lembretesAtualizados);
 localStorage.setItem('lembretes', JSON.stringify(lembretesAtualizados));
 };

 return (
 <View>
 <Text>Lembra-me</Text>
 <FlatList
 data={lembretes}
 renderItem={({ item }) => (
 <View>
 <Text>{item.texto}</Text>
 <TouchableOpacity onPress={() => marcarConcluido((link unavailable))}>
 <Text>Concluir</Text>
 </TouchableOpacity>
 <TouchableOpacity onPress={() => excluirLembrete((link unavailable))}>
 <Text>Excluir</Text>
 </TouchableOpacity>
 </View>
 )}
 />
 <TextInput
 value={novoLembrete}
 onChangeText={(texto) => setNovoLembrete(texto)}
 placeholder="Novo lembrete"
 />
 <TouchableOpacity onPress={adicionarLembrete}>
 <Text>Adicionar</Text>
 </TouchableOpacity>
 </View>
 );
};
