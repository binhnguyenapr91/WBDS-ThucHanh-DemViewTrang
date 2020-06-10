#### [Thực hành] Đếm số lượt view trang
###### Mục tiêu  
Luyện tập triển khai cơ chế session trong Spring MVC.

###### Mô tả
Trong phần này, chúng ta sẽ phát triển một tính năng cho phép ghi nhận số lần người dùng truy cập trang web trong một phiên làm việc.

Ứng dụng sẽ ghi nhận và hiển thị số lần truy cập. Khi người dùng truy cập vào một trang trong ứng dụng thì số lần truy cập sẽ tăng lên.

```
@Controller
@SessionAttributes("mycounter")
public class CounterController {
    @ModelAttribute("mycounter")
    MyCounter getCouter() {
        return new MyCounter();
    }

    @GetMapping("/")
    String increment(@ModelAttribute("mycounter") MyCounter myCounter){
        myCounter.increment();
        return "index";
    }
}
```

- Annotation @SessionAttributes("mycounter") được sử dụng để lưu trữ model attribute trong session. 
- Trong đoạn mã trên, model attribute "mycounter"  sẽ được thêm vào session nếu tên attribute của @ModelAttribute và @SessionAttributes giống nhau.
- Annotation @ModelAttribute liên kết một tham số phương thức hoặc một phương thức trả về giá trị cho một model attribute và sau đó trả nó về một view cụ thể.
- Hàm increment() có nhiệm vụ tăng giá trị thuộc tính count của đối tượng myCounter