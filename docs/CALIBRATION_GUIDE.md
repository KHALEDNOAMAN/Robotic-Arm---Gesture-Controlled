# Gesture-Controlled Robotic Arm - Calibration & Troubleshooting

## Sensor Glove Calibration

### Flex Sensor Setup
| Finger | Analog Pin | Min Value | Max Value |
|--------|-----------|-----------|-----------|
| Thumb | A0 | 200 | 800 |
| Index | A1 | 180 | 780 |
| Middle | A2 | 190 | 790 |
| Ring | A3 | 200 | 810 |
| Pinky | A4 | 210 | 800 |

### Calibration Steps
1. Upload calibration sketch
2. Open Serial Monitor (9600 baud)
3. Fully extend each finger - record MIN value
4. Fully close each finger - record MAX value
5. Update values in config.h

## Servo Mapping
| Joint | Servo | Range | Default |
|-------|-------|-------|---------|
| Base rotation | MG996R | 0-180 | 90 |
| Shoulder | MG996R | 30-150 | 90 |
| Elbow | SG90 | 0-180 | 90 |
| Wrist | SG90 | 0-180 | 90 |
| Gripper | SG90 | 10-80 | 10 |

## Troubleshooting
| Problem | Cause | Fix |
|---------|-------|-----|
| Servo jittering | Insufficient power | Use separate 5V supply |
| Erratic movement | Noise on ADC | Add 100nF capacitor to flex sensor |
| Gripper not closing | Servo range too small | Adjust map() bounds |
| Arm drifting | Loose connections | Check wiring + add pullup resistors |
| No response | Serial conflict | Verify baud rate matches |

## Power Requirements
- Arduino: 5V USB
- Servos: External 5V 3A supply (DO NOT power from Arduino)
- Flex sensors: 3.3V from Arduino + 10K pulldown resistors

## Future 4-Link Expansion
- Add 2 more servos for wrist pitch/yaw
- Upgrade to PCA9685 PWM driver (16 channels)
- Add IMU (MPU6050) for orientation tracking