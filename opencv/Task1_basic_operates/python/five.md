import cv2


def mark_material_contour_and_center(cap):
    while True:
        ret, frame = cap.read()
        if not ret:
            break
        # 转换为灰度图像
        gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
        # 边缘检测
        edges = cv2.Canny(gray, 50, 150)
        # 查找轮廓
        contours, _ = cv2.findContours(edges, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)
        for contour in contours:
            # 绘制白色轮廓（可根据需求调整颜色）
            cv2.drawContours(frame, [contour], -1, (255, 255, 255), 2)
            # 计算轮廓的外接矩形
            x, y, w, h = cv2.boundingRect(contour)
            # 计算外接矩形的中心
            center_x = x + w // 2
            center_y = y + h // 2
            # 绘制十字标记中心
            cv2.line(frame, (center_x - 10, center_y), (center_x + 10, center_y), (0, 255, 0), 2)
            cv2.line(frame, (center_x, center_y - 10), (center_x, center_y + 10), (0, 255, 0), 2)
        cv2.imshow('Material Marking', frame)
        if cv2.waitKey(1) & 0xFF == ord('q'):
            break
    cap.release()
    cv2.destroyAllWindows()


cap = cv2.VideoCapture(0)  # 0表示默认摄像头
mark_material_contour_and_center(cap)

cv2.waitKey(0)
cv2.destroyAllWindows()