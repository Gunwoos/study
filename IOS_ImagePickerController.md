# Image Picker Controller
- 사진이 동영상을 촬영하고 그 데이터를 저장하거나 사용하기 위함
- 사용자의 사진 앨범에서 사진을을 불러올 수도 있음

### ImagePickerController 생성
```
private let imagePickerController = UIImagePickerController()
imagePickerController.delegate = self
/*
에러메세지가 나오지 않게 하기 위해 UIImagePickerController 을 등록할 viewController 에 
UIImagePickerControllerDelegate, UINavigationControllerDelegate 을 extension 해주어야 함
*/

```
- 사진 가져오기
```
  let type = UIImagePickerControllerSourceType.photoLibrary
  guard UIImagePickerController.isSourceTypeAvailable(type) else { return }
    
  imagePickerController.sourceType = type
```
- 카메라 사용하기
```
  guard UIImagePickerController.isSourceTypeAvailable(.camera) else { return }
  imagePickerController.sourceType = .camera
    
  present(imagePickerController, animated: true)
```
- 앨범에 불러온 사진이나 직접 촬영한 사진이나 동영상은 delegate 에서 다뤄야함

### ImagePickerController Sample code

```
//
//  ViewController.swift
//  ImagePickerControllerExample
//
//  Created by giftbot on 2018. 7. 5..
//  Copyright © 2018년 giftbot. All rights reserved.
//

import UIKit
import MobileCoreServices

final class ViewController: UIViewController {

  @IBOutlet private weak var imageView: UIImageView!
  private let imagePickerController = UIImagePickerController()
  
  override func viewDidLoad() {
    super.viewDidLoad()
    
    imagePickerController.delegate = self
    
  }
  
  @IBAction private func pickImage(_ sender: Any) {
    print("\n---------- [ pickImage ] ----------\n")
    let type = UIImagePickerControllerSourceType.photoLibrary
    guard UIImagePickerController.isSourceTypeAvailable(type) else { return }
    
    imagePickerController.sourceType = type
    present(imagePickerController, animated: true)
  }
  
  
  @IBAction private func takePicture(_ sender: Any) {
    print("\n---------- [ takePicture ] ----------\n")
    guard UIImagePickerController.isSourceTypeAvailable(.camera) else { return }
    imagePickerController.sourceType = .camera
    
    present(imagePickerController, animated: true)
  }
  
  @IBAction private func takePictureWithDelay(_ sender: Any) {
    print("\n---------- [ takePictureWithDelay ] ----------\n")
    guard UIImagePickerController.isSourceTypeAvailable(.camera) else { return }
    imagePickerController.sourceType = .camera
    
    
    // public.image
    print(imagePickerController.mediaTypes)
    
    // [public.image, public.movie]
    print(UIImagePickerController.availableMediaTypes(for: .camera) ?? [])
    
    imagePickerController.mediaTypes = ["public.image","public.movie"]
    imagePickerController.mediaTypes = [kUTTypeImage as String, kUTTypeMovie as String]
    
    // kUTTypeImage
    // kUTTypeVideo // video o , audio x
    // kUTTypeMovie // video o , audio o
    
    present(
    imagePickerController, animated: true){
        self.imagePickerController.takePicture()
    }
    
//    present(imagePickerController, animated: true){ [weak self] in
//        DispatchQueue.main.asyncAfter(deadline: .now() + 3, execute:{
//            self?.imagePickerController.takePicture()
//        })
//    }

  }
  
  
  @IBAction private func recordingVideo(_ sender: Any) {
    print("\n---------- [ recordingVideo ] ----------\n")
    
    guard UIImagePickerController.isSourceTypeAvailable(.camera) else { return }
    imagePickerController.sourceType = .camera
    imagePickerController.mediaTypes = [kUTTypeMovie as String]
    imagePickerController.cameraCaptureMode = .video
    
    imagePickerController.cameraDevice = .front
    imagePickerController.cameraFlashMode = .auto
    
    present(imagePickerController, animated: true)
    
    
  }
  
  @IBAction private func toggleAllowsEditing(_ sender: Any) {
    print("\n---------- [ toggleAllowsEditing ] ----------\n")
    imagePickerController.allowsEditing = !imagePickerController.allowsEditing
  }
    
    
    
}


extension ViewController: UIImagePickerControllerDelegate, UINavigationControllerDelegate{
    // delegate 미구현 시 종료되도록 구현 되어있음
    func imagePickerController(_ picker: UIImagePickerController, didFinishPickingMediaWithInfo info: [String : Any]) {
        print("")
        
        let mediaType = info[UIImagePickerControllerMediaType] as! NSString
        if UTTypeEqual(mediaType, kUTTypeMovie){
            //move
            let originalVideo = info[UIImagePickerControllerMediaURL] as! NSURL
            
            if let path = originalVideo.path{
                UISaveVideoAtPathToSavedPhotosAlbum(path, nil, nil, nil)
            }
                
        }
        else{
            // image
            let originalImage = info[UIImagePickerControllerOriginalImage] as? UIImage
            let editedImage = info[UIImagePickerControllerEditedImage] as? UIImage
            let selectedImage = editedImage ?? originalImage
            imageView.image = selectedImage
            
            if let saveImage = selectedImage{
                UIImageWriteToSavedPhotosAlbum(saveImage, nil, nil, nil)
            }
        }
    

        
        picker.dismiss(animated: true)
    }
    func imagePickerControllerDidCancel(_ picker: UIImagePickerController) {
        print("")
        picker.dismiss(animated: true)
    }
    
    
    
}

```
