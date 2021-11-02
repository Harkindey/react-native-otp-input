## Usage

```js
import OTPInputView from 'react-native-otp-input'
 const [otpError, setotpError] = useState(false);

   const authenticate = async (code: string) => {
    try {
      await otpAuthorization({ otp: code });
    } catch (error) {
      ReactNativeHapticFeedback.trigger('impactHeavy', options); //vibration to let user know pin error occured just a UX choice
      setotpError(true);
    }
  };

...

        <OTPInputView
          pinCount={6}
          style={styles.OTPInputView}
          autoFocusOnLoad={true}
          codeInputFieldStyle={{
            ...styles.codeInputFieldStyle,
            ...(otpError && { borderColor: theme.red }),
          }}
          codeInputHighlightStyle={{
            ...styles.codeInputHighlightStyle,
            ...(otpError && { borderColor: theme.red }),
          }}
          keyboardType="number-pad"
          onCodeFilled={code => {
            authenticate(code);
          }}
          // code={this.state.code} //You can supply this prop or not. The component will be used as a controlled / uncontrolled component respectively.
          // onCodeChanged = {code => { this.setState({code})}}
          onCodeChanged={() => setotpError(false)} // revert error once user starts typing again alternative to onFocus/onBlur
          filledCodeInputFieldStyle={{
            color: theme.primaryColor,
            borderColor: theme.primaryColor,
            backgroundColor: theme.secondaryColor,
            ...(otpError && { borderColor: theme.red }),
          }}
        />

const styles = StyleSheet.create({
  borderStyleBase: {
    width: 30,
    height: 45
  },

  borderStyleHighLighted: {
    borderColor: "#03DAC6",
  },

  underlineStyleBase: {
    width: 30,
    height: 45,
    borderWidth: 0,
    borderBottomWidth: 1,
  },

  underlineStyleHighLighted: {
    borderColor: "#03DAC6",
  },
});

```

## Parameters

| Parameter                 | required | Description                                                                                     |
| ------------------------- | -------- | ----------------------------------------------------------------------------------------------- |
| pinCount                  | YES      | Number of digits in the component                                                               |
| code                      | NO       | You can use this library as a controlled / uncontrolled component by supplying this prop or not |
| codeInputFieldStyle       | NO       | The style of the input field which is NOT focused                                               |
| codeInputHighlightStyle   | NO       | The style of the input field which is focused                                                   |
| autoFocusOnLoad           | NO       | Auto activate the input and bring up the keyboard when component is loaded                      |
| onCodeChanged             | NO       | Callback when the digits are changed                                                            |
| onCodeFilled              | NO       | Callback when the last digit is entered                                                         |
| secureTextEntry           | NO       | Hide contents of text fields                                                                    |
| editable                  | NO       | Set editable for inputs                                                                         |
| keyboardAppearance        | NO       | Keyboard appearance ('default', 'dark', 'light')                                                |
| keyboardType              | NO       | Keyboard type                                                                                   |
| clearInputs               | NO       | Clear inputs after entering code                                                                |
| placeholderCharacter      | NO       | The character/string that will be used as placeholder in the individual code input fields       |
| placeholderTextColor      | NO       | Color of the placeholderCharacter                                                               |
| filledCodeInputFieldStyle | NO       | Style of a filled input field                                                                   |
