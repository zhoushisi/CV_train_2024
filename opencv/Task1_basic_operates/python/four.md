import cv2

from third import resize_phone_image


def save_color_spaces():
    # 读取 all.jpg 图片
    image = cv2.imread('all.jpg')

    # 保存为灰度图
    gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
    cv2.imwrite('all_gray.jpg', gray_image)
    resize_phone_image()

    # 保存为 HSV 图
    hsv_image = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)
    cv2.imwrite('all_hsv.jpg', hsv_image)

    # 保存为 Lab 图
    lab_image = cv2.cvtColor(image, cv2.COLOR_BGR2Lab)
    cv2.imwrite('all_lab.jpg', lab_image)

if __name__ == "__main__":
   save_color_spaces()  # 在这里调用函数，启动图像保存相关操作流程

cv2.waitKey(0)
