Code for the app 

```
import React, { useState } from 'react';
import { View, Text, TextInput, TouchableOpacity, StyleSheet, Alert } from 'react-native';

export default function CalculatorApp() {
  const [num1, setNum1] = useState('');
  const [num2, setNum2] = useState('');
  const [result, setResult] = useState(null);

  const handleCalculation = (operation) => {
    const number1 = parseFloat(num1);
    const number2 = parseFloat(num2);

    if (isNaN(number1) || isNaN(number2)) {
      Alert.alert('Error', 'Please enter valid numbers');
      return;
    }

    let calculationResult;
    switch (operation) {
      case 'Add':
        calculationResult = number1 + number2;
        break;
      case 'Subtract':
        calculationResult = number1 - number2;
        break;
      case 'Multiply':
        calculationResult = number1 * number2;
        break;
      case 'Divide':
        if (number2 === 0) {
          Alert.alert('Error', 'Division by zero is not allowed');
          return;
        }
        calculationResult = number1 / number2;
        break;
      case 'Power':
        calculationResult = Math.pow(number1, number2);
        break;
      case 'SquareRoot':
        if (number1 < 0) {
          Alert.alert('Error', 'Square root of a negative number is not allowed');
          return;
        }
        calculationResult = Math.sqrt(number1);
        break;
      default:
        calculationResult = null;
    }
    setResult(calculationResult);
  };

  return (
    <View style={styles.container}>
      <Text style={styles.heading}>Calculator App</Text>
      <TextInput
        style={styles.input}
        placeholder="Enter first number"
        keyboardType="numeric"
        value={num1}
        onChangeText={(text) => setNum1(text)}
      />
      <TextInput
        style={styles.input}
        placeholder="Enter second number"
        keyboardType="numeric"
        value={num2}
        onChangeText={(text) => setNum2(text)}
      />
      <View style={styles.buttonContainer}>
        <TouchableOpacity style={styles.button} onPress={() => handleCalculation('Add')}>
          <Text style={styles.buttonText}>Add</Text>
        </TouchableOpacity>
        <TouchableOpacity style={styles.button} onPress={() => handleCalculation('Subtract')}>
          <Text style={styles.buttonText}>Subtract</Text>
        </TouchableOpacity>
        <TouchableOpacity style={styles.button} onPress={() => handleCalculation('Multiply')}>
          <Text style={styles.buttonText}>Multiply</Text>
        </TouchableOpacity>
        <TouchableOpacity style={styles.button} onPress={() => handleCalculation('Divide')}>
          <Text style={styles.buttonText}>Divide</Text>
        </TouchableOpacity>
        <TouchableOpacity style={styles.button} onPress={() => handleCalculation('Power')}>
          <Text style={styles.buttonText}>To the Power Of</Text>
        </TouchableOpacity>
        <TouchableOpacity style={styles.button} onPress={() => handleCalculation('SquareRoot')}>
          <Text style={styles.buttonText}>Square Root</Text>
        </TouchableOpacity>
      </View>
      {result !== null && (
        <Text style={styles.result}>Result: {result}</Text>
      )}
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    padding: 20,
  },
  heading: {
    fontSize: 24,
    marginBottom: 20,
    textAlign: 'center',
  },
  input: {
    height: 40,
    borderColor: 'gray',
    borderWidth: 1,
    marginBottom: 10,
    paddingHorizontal: 10,
  },
  buttonContainer: {
    flexDirection: 'row',
    flexWrap: 'wrap',
    justifyContent: 'space-between',
    marginTop: 20,
  },
  button: {
    backgroundColor: '#007BFF',
    padding: 10,
    width: '48%',
    marginBottom: 10,
    justifyContent: 'center',
    alignItems: 'center',
  },
  buttonText: {
    color: '#fff',
    fontSize: 18,
  },
  result: {
    marginTop: 20,
    fontSize: 24,
    textAlign: 'center',
  },
});

```
