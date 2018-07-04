```
//
//  ViewController.swift
//  URLScheme
//
//  Created by giftbot on 2018. 7. 2..
//  Copyright © 2018년 giftbot. All rights reserved.
//

import UIKit

final class ViewController: UIViewController {
  
  @IBAction private func openSetting(_ sender: Any) {
    print("\n---------- [ openSettingApp ] ----------\n")
    
    guard let settingURL = URL(string: UIApplicationOpenSettingsURLString),
        UIApplication.shared.canOpenURL(settingURL)
        else{return}
    
    if #available(iOS 10.0, *){
        UIApplication.shared.open(settingURL)
    }
    else{
        UIApplication.shared.openURL(settingURL)
    }
  }
  
  @IBAction private func openMail(_ sender: Any) {
    print("\n---------- [ openMail ] ----------\n")
    
    guard let mailURL = URL(string: "mailto://") else { return }
    
    if UIApplication.shared.canOpenURL(mailURL){
        UIApplication.shared.open(mailURL)
    }
    
  }

  @IBAction private func openMessage(_ sender: Any) {
    print("\n---------- [ openMessage ] ----------\n")
    
//    guard let messageURL = URL(string: "sms:") else{return}
    guard let messageURL = URL(string: "sms://010-9999-9999") else{return}
    
    if UIApplication.shared.canOpenURL(messageURL){
        UIApplication.shared.open(messageURL)
    }
  }
  
  @IBAction private func openWebsite(_ sender: Any) {
    print("\n---------- [ openWebsite ] ----------\n")
    
    guard let websiteURL = URL(string: "https://naver.com") else{return}
    
    if UIApplication.shared.canOpenURL(websiteURL){
        UIApplication.shared.open(websiteURL)
    }
  }
  
  @IBAction private func openFacebook(_ sender: Any) {
    print("\n---------- [ openFacebook ] ----------\n")
    
    guard let facebookScheme = URL(string: "fb://") else { return }
    
    if UIApplication.shared.canOpenURL(facebookScheme){
        UIApplication.shared.open(facebookScheme)
    }
  }
  
  @IBAction private func openMyApp(_ sender: Any) {
    print("\n---------- [ openMyApp ] ----------\n")
    
    guard let myAppScheme = URL(string: "myApp://?name=abc&age=10") else { return }
    
    if UIApplication.shared.canOpenURL(myAppScheme){
        UIApplication.shared.open(myAppScheme)
    }
    
  }
}

/*
 전화 - tel://010-0000-0000
 페이스타임 - facetime://010-0000-0000
 애플맵 검색 텍스트 - http://maps.apple.com?q=searchText
 애플맵 (위경도 지정) - http://maps.apple.com/?ll=latitude,longitude
 앱스토어 (구글맵) - https://itunes.apple.com/kr/app/google-maps/id5850273547mt=8
 유투브 - https://www.youtube.com/watch?v=BzYnNdJhZQw
*/



```
