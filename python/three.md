import cv2

def resize_phone_image():
    # 读取 all.jpg 和 phone.jpg 图片
    phone_image = cv2.imread('photo.jpg')
    all_image = cv2.imread('all.jpg')
    if all_image is None:
        print("无法读取图像，请检查图像路径是否正确。")
    else:
        # 获取 all.jpg 的完整尺寸
        all_height, all_width, all_depth = all_image.shape
        print(f"图像的高度为: {all_height}，宽度为: {all_width}，深度为: {all_depth}")
        # 调整 phone.jpg 的尺寸
        resized_phone_image = cv2.resize(phone_image, (all_width, all_height))
        # 保存调整后的图片为 phone_resized.jpg
        cv2.imwrite( 'phone_resized.jpg', resized_phone_image)

resize_phone_image()
cv2.waitKey(0)
