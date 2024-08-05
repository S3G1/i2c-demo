# i2c-demo
Output of the application:
![image](https://github.com/user-attachments/assets/1577a141-12a0-4eb2-a38b-4972bd7ac4a3)
I2C protocol is in use to create connection between ENS160 and STM32 and UART protocol is in use in order to create connection between stm32 and PC.



uint8_t data[2];                                                                                    // buffet to store the data from sensor
HAL_I2C_Mem_Read(&hi2c1,sensor_address << 1, register_address,I2C_MEMADD_SIZE_8BIT, data, 2, 1000); // function to get the data from sensor
uint16_t eCO = (data[0] << 8) | data[1];                                                            // eCo is two bytes so when we receive 8 
                                                                                                       bits we have to shift these two bits to
                                                                                                      the left and join first byte and second     
                                                                                                      byte together. So we can have 16 bits
 HAL_UART_Transmit(&huart2,(uint8_t*)buffer,strlen(buffer), HAL_MAX_DELAY);                          // this function is used to send the data from 
                                                                                                         stm32 to pc via UART protocol.
