import cv2

# 打开电脑摄像头
cap = cv2.VideoCapture(0)

# 检查摄像头是否成功打开
if not cap.isOpened():
    print("无法打开摄像头")
    exit()

# 循环读取摄像头画面
while True:
    ret, frame = cap.read()

    # 如果读取帧失败，退出循环
    if not ret:
        print("读取帧失败")
        break

    # 显示摄像头画面
    cv2.imshow('all', frame)

    # 按下 's' 键保存图片
    if cv2.waitKey(1) == ord('s'):
        # 当按下 's' 键时
        cv2.imwrite('all.jpg', frame)
        #重命名为all.jpg
        print("图片已保存为 all.jpg")
        break
    if cv2.waitKey(1) & 0xFF == ord('q'):
        # 当按下 'q' 键时
        break  # 退出循环
# 释放摄像头资源
cap.release()

# 关闭所有窗口
cv2.destroyAllWindows()
