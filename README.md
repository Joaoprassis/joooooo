Atualizar calendário
import React from 'react';
import { View, Text, StyleSheet, ScrollView, TouchableOpacity } from 'react-native';
import { Ionicons } from '@expo/vector-icons'; // Para ícones

export default function ActivityScreen() {
  return (
    <View style={styles.container}>
      {/* Header com os dias da semana */}
      <ScrollView horizontal showsHorizontalScrollIndicator={false} style={styles.header}>
        {['S', 'M', 'T', 'W', 'T', 'F', 'S'].map((day, index) => (
          <TouchableOpacity key={index} style={[styles.day, index === 3 && styles.selectedDay]}>
            <Text style={[styles.dayText, index === 3 && styles.selectedDayText]}>{day}</Text>
            {index === 3 && <View style={styles.selectedIndicator}></View>}
          </TouchableOpacity>
        ))}
      </ScrollView>

      {/* Cards das atividades */}
      <ScrollView style={styles.activities}>
        {[
          { icon: 'walk-outline', color: '#FF8C00', title: 'Walking', value: '9857 Steps', time: 'Today 11:45 AM' },
          { icon: 'fitness-outline', color: '#FF69B4', title: 'Workout', value: '45 minutes', time: 'Today 8:00 PM' },
          { icon: 'bicycle-outline', color: '#1E90FF', title: 'Cycling', value: '17 km', time: 'Today 6:00 AM' },
          { icon: 'barbell-outline', color: '#FFD700', title: 'Push-ups', value: '230', time: 'Today 9:00 AM' },
        ].map((activity, index) => (
          <View key={index} style={styles.card}>
            <View style={[styles.iconContainer, { backgroundColor: activity.color }]}>
              <Ionicons name={activity.icon} size={24} color="#fff" />
            </View>
            <View style={styles.info}>
              <Text style={styles.title}>{activity.title}</Text>
              <Text style={styles.value}>{activity.value}</Text>
              <Text style={styles.time}>{activity.time}</Text>
            </View>
          </View>
        ))}
      </ScrollView>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#F5F5F5',
    padding: 16,
  },
  header: {
    marginBottom: 20,
  },
  day: {
    alignItems: 'center',
    marginHorizontal: 8,
  },
  selectedDay: {
    borderBottomWidth: 2,
    borderColor: '#6A0DAD',
  },
  dayText: {
    fontSize: 16,
    color: '#A9A9A9',
  },
  selectedDayText: {
    color: '#6A0DAD',
  },
  activities: {
    marginTop: 10,
  },
  card: {
    flexDirection: 'row',
    alignItems: 'center',
    backgroundColor: '#fff',
    padding: 16,
    borderRadius: 12,
    marginBottom: 10,
    shadowColor: '#000',
    shadowOffset: { width: 0, height: 2 },
    shadowOpacity: 0.1,
    shadowRadius: 8,
    elevation: 2,
  },
  iconContainer: {
    width: 50,
    height: 50,
    borderRadius: 25,
    justifyContent: 'center',
    alignItems: 'center',
  },
  info: {
    marginLeft: 16,
  },
  title: {
    fontSize: 18,
    fontWeight: 'bold',
    color: '#333',
  },
  value: {
    fontSize: 16,
    color: '#555',
  },
  time: {
    fontSize: 14,
    color: '#A9A9A9',
  },
});




Tela de exercioss******
import React, { useState } from 'react';
import { View, Text, StyleSheet, TouchableOpacity, Image, Button } from 'react-native';

const CorridaScreen = () => {
  const [distance, setDistance] = useState(0.25);

  const increaseDistance = () => {
    setDistance((prev) => parseFloat((prev + 0.25).toFixed(2)));
  };

  const decreaseDistance = () => {
    setDistance((prev) => (prev > 0.25 ? parseFloat((prev - 0.25).toFixed(2)) : prev));
  };

  return (
    <View style={styles.container}>
      {/* Cabeçalho */}
      <Text style={styles.title}>Exercícios e Atividade Física</Text>
      <Text style={styles.subtitle}>
        Escolha seu tempo praticando e veja seu desempenho total.
      </Text>

      {/* Imagem */}
      <Image
        source={{ uri: 'https://via.placeholder.com/300x200?text=Ilustracao' }} // Substitua pela URL da imagem real
        style={styles.image}
        resizeMode="contain"
      />

      {/* Objetivo */}
      <Text style={styles.sectionTitle}>Seu objetivo</Text>
      <View style={styles.goalContainer}>
        <TouchableOpacity style={styles.button} onPress={decreaseDistance}>
          <Text style={styles.buttonText}>-</Text>
        </TouchableOpacity>
        <Text style={styles.distance}>{distance} km</Text>
        <TouchableOpacity style={styles.button} onPress={increaseDistance}>
          <Text style={styles.buttonText}>+</Text>
        </TouchableOpacity>
      </View>

      {/* Exercício */}
      <Text style={styles.exerciseLabel}>Exercício</Text>

      {/* Botão de Iniciar */}
      <TouchableOpacity style={styles.startButton}>
        <Text style={styles.startButtonText}>Iniciar</Text>
      </TouchableOpacity>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#F5F5F5',
    alignItems: 'center',
    padding: 20,
  },
  title: {
    fontSize: 24,
    fontWeight: 'bold',
    color: '#333',
    textAlign: 'center',
    marginTop: 20,
  },
  subtitle: {
    fontSize: 14,
    color: '#666',
    textAlign: 'center',
    marginVertical: 10,
  },
  image: {
    width: 300,
    height: 200,
    marginVertical: 20,
  },
  sectionTitle: {
    fontSize: 16,
    fontWeight: 'bold',
    color: '#333',
    marginVertical: 10,
  },
  goalContainer: {
    flexDirection: 'row',
    alignItems: 'center',
    justifyContent: 'center',
    marginVertical: 20,
  },
  button: {
    width: 50,
    height: 50,
    borderRadius: 25,
    backgroundColor: '#E0E0E0',
    justifyContent: 'center',
    alignItems: 'center',
  },
  buttonText: {
    fontSize: 24,
    color: '#333',
  },
  distance: {
    fontSize: 24,
    fontWeight: 'bold',
    color: '#333',
    marginHorizontal: 20,
  },
  exerciseLabel: {
    fontSize: 16,
    color: '#333',
    marginBottom: 20,
  },
  startButton: {
    backgroundColor: '#4CAF50',
    borderRadius: 8,
    paddingVertical: 15,
    paddingHorizontal: 80,
    alignItems: 'center',
    justifyContent: 'center',
    marginTop: 30,
  },
  startButtonText: {
    fontSize: 18,
    color: '#FFF',
    fontWeight: 'bold',
  },
});

export default CorridaScreen;
