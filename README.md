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
