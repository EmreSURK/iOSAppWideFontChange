# iOSAppWideFontChange
Steps;
1. Copy fonts to Project with "Copyh if needed" tick.
2. Paste the code below.
3. Add font to info.plist. 



"""



	<key>UIAppFonts</key>
	<array>
		<string>Montserrat-Thin.ttf</string>
		<string>Montserrat-BlackItalic.ttf</string>
		<string>Montserrat-Black.ttf</string>
		<string>Montserrat-ExtraBoldItalic.ttf</string>
		<string>Montserrat-ExtraBold.ttf</string>
		<string>Montserrat-BoldItalic.ttf</string>
		<string>Montserrat-Bold.ttf</string>
		<string>Montserrat-SemiBoldItalic.ttf</string>
		<string>Montserrat-SemiBold.ttf</string>
		<string>Montserrat-MediumItalic.ttf</string>
		<string>Montserrat-Medium.ttf</string>
		<string>Montserrat-Italic.ttf</string>
		<string>Montserrat-Regular.ttf</string>
		<string>Montserrat-LightItalic.ttf</string>
		<string>Montserrat-Light.ttf</string>
		<string>Montserrat-ExtraLightItalic.ttf</string>
		<string>Montserrat-ExtraLight.ttf</string>
		<string>Montserrat-ThinItalic.ttf</string>
	</array>



    for family in UIFont.familyNames.sorted() {
        let names = UIFont.fontNames(forFamilyName: family)
        print("Family: \(family) Font names: \(names)")
    }
    
    // Console output will be like: Family: Greycliff CF Font names: ["GreycliffCF-MediumOblique", "GreycliffCF-BoldOblique", "GreycliffCF-Light", "GreycliffCF-RegularOblique", "GreycliffCF-LightOblique", "GreycliffCF-HeavyOblique", "GreycliffCF-Bold", "GreycliffCF-ExtraBoldOblique", "GreycliffCF-Regular", "GreycliffCF-Medium", "GreycliffCF-ExtraBold", "GreycliffCF-DemiBold", "GreycliffCF-DemiBoldOblique", "GreycliffCF-Heavy"]
    
    
    let font = UIFont(name: "Greycliff CF", size: UIFont.systemFontSize)!
						   
    UILabel.appearance().substituteFontName = "GreycliffCF"
    UITextField.appearance().substituteFontName = "GreycliffCF"

    UIButton.appearance().titleLabel?.font = font
    UITabBarItem.appearance().setTitleTextAttributes([ NSAttributedString.Key.font : font.withSize(11) ], for: .normal)
    
    

    extension UILabel {
      @objc var substituteFontName : String {
        get {
          return self.font.fontName;
        }
        set {
          let fontNameToTest = self.font.fontName.lowercased();
          var fontName = newValue;
          if fontNameToTest.range(of: "bold") != nil {
            fontName += "-Bold";
          } else if fontNameToTest.range(of: "medium") != nil {
            fontName += "-Medium";
          } else if fontNameToTest.range(of: "light") != nil {
            fontName += "-Light";
          } else if fontNameToTest.range(of: "ultralight") != nil {
            fontName += "-UltraLight";
          }else if fontNameToTest.range(of: "ultralight") != nil {
            fontName += "-UltraLight";
          }else if fontNameToTest.range(of: "semibold") != nil {
            fontName += "-DemiBold";
          }
          self.font = UIFont(name: fontName, size: self.font.pointSize)
        }
      }
    }

    extension UITextView {
      @objc var substituteFontName : String {
        get {
          return self.font?.fontName ?? "";
        }
        set {
          let fontNameToTest = self.font?.fontName.lowercased() ?? "";
          var fontName = newValue;
          if fontNameToTest.range(of: "bold") != nil {
            fontName += "-Bold";
          } else if fontNameToTest.range(of: "medium") != nil {
            fontName += "-Medium";
          } else if fontNameToTest.range(of: "light") != nil {
            fontName += "-Light";
          } else if fontNameToTest.range(of: "ultralight") != nil {
            fontName += "-UltraLight";
          }
          self.font = UIFont(name: fontName, size: self.font?.pointSize ?? 17)
        }
      }
    }

    extension UITextField {
      @objc var substituteFontName : String {
        get {
          return self.font?.fontName ?? "";
        }
        set {
          let fontNameToTest = self.font?.fontName.lowercased() ?? "";
          var fontName = newValue;
          if fontNameToTest.range(of: "bold") != nil {
            fontName += "-Bold";
          } else if fontNameToTest.range(of: "medium") != nil {
            fontName += "-Medium";
          } else if fontNameToTest.range(of: "light") != nil {
            fontName += "-Light";
          } else if fontNameToTest.range(of: "ultralight") != nil {
            fontName += "-UltraLight";
          }
          self.font = UIFont(name: fontName, size: self.font?.pointSize ?? 17)
        }
      }
    }
