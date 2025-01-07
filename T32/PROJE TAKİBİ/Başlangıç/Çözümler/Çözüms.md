const DismissKeyboard = ({ children }: any) => (

  <TouchableWithoutFeedback onPress={() => Keyboard.dismiss()}>

    {children}

  </TouchableWithoutFeedback>

)


tsconfig olayında ctrl+shift+P  restart ts server

genel manada da reload window