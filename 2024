<script> 
var citis = document.getElementById("TinhThanhPhoSelect");
var districts = document.getElementById("QuanHuyenSelect");
var wards = document.getElementById("ward");
var Parameter = {
  url: "https://raw.githubusercontent.com/Truong-Nobi/JsTinhThanhPho2025/refs/heads/main/hanhchinh3cap2024.json", //Đường dẫn đến file chứa dữ liệu hoặc api do backend cung cấp
  method: "GET", //do backend cung cấp
  responseType: "application/json", //kiểu Dữ liệu trả về do backend cung cấp
};
//gọi ajax = axios => nó trả về cho chúng ta là một promise
var promise = axios(Parameter);
//Xử lý khi request thành công
promise.then(function(result) {
  renderCity(result.data);
});
function renderCity(data) {
  for(const x of data) {
    citis.options[citis.options.length] = new Option(x.Name, x.Id);
  }
  // xứ lý khi thay đổi tỉnh thành thì sẽ hiển thị ra quận huyện thuộc tỉnh thành đó
  citis.onchange = function() {
    QuanHuyenSelect.length = 1;
    ward.length = 1;
    if(this.value != "") {
      const result = data.filter(n => n.Id === this.value);
      for(const k of result[0].Districts) {
        QuanHuyenSelect.options[QuanHuyenSelect.options.length] = new Option(k.Name, k.Id);
      }
    }
  };
  // xứ lý khi thay đổi quận huyện thì sẽ hiển thị ra phường xã thuộc quận huyện đó
  QuanHuyenSelect.onchange = function() {
    ward.length = 1;
    const dataCity = data.filter((n) => n.Id === citis.value);
    if(this.value != "") {
      const dataWards = dataCity[0].Districts.filter(n => n.Id === this.value)[0].Wards;
      for(const w of dataWards) {
        wards.options[wards.options.length] = new Option(w.Name, w.Id);
      }
    }
  };
}
  function AutoUpdateAdress(trigger_element) { 
document.getElementById("TinhThanhPho").value = $("#TinhThanhPhoSelect option:selected").text();
document.getElementById("QuanHuyen").value = $("#QuanHuyenSelect option:selected").text();
}
</script>

<!-- HTML MODAL ĐĂNG NHẬP / ĐĂNG KÝ -->
<div class="allModalShow" id="modalProductShowDangNhap">
  <div class="allModalShow-content">
    <div class="allModalShow-footer d-flex">
      <button class="buttonStyle2 click-btn d-flex" onclick="closeAllModal()" style="margin: 0;height: auto;">Đóng [&#10006;]</button>
    </div>
    <div class="allModalShowBody">
      <div class="form">
        <ul class="tab-group">
          <li id="dangKiForm" class="tab d-flex active" onclick="openFormDangKi()">
            <p>Đăng kí</p>
          </li>
          <li id="dangNhapForm" class="tab d-flex" onclick="openFormDangNhap()">
            <p>Đăng nhập</p>
          </li>
        </ul>
        <div class="tab-content">
          <div id="signup" style="border-radius: 5px;border: 2px #f99911 dashed;padding: 0.5em;">
            <p style="color: white;font-size: 18px;text-align: center;margin: 0px;">Đăng kí miễn phí</p>
            <form action="https://docs.google.com/forms/d/e/1FAIpQLSfC6eG8XU8D6GsgHtnzYU8qUlMJZ5POYvRK8bBGvJdicjPYRA/formResponse?embedded=true" class="fieldset" id="FormDangKi" method="POST" name="myForm" target="hidden_iframe">
              <div class="field field-third">
                <div class="field-input-wrapper">
                  <input autocapitalize="off" class="field-input" id="HoTen" name="entry.59372100" placeholder="Họ và tên" required="" size="30" type="text" value="" />
                </div>
                <div class="mota">Họ và tên</div>
              </div>
              <div class="field field-third">
                <div class="field-input-wrapper">
                  <input autocapitalize="off" required="" class="field-input" id="TenTaiKhoan" name="entry.295871689" placeholder="Tên tài khoản" size="30" onkeyup="this.value=this.value.replace(/[^a-z0-9]/g,'')" type="text" value="" />
                </div>
                <div class="mota">Tên tài khoản [Bao gồm chữ thường và số]</div>
              </div>
              <div class="field field-third">
                <div class="field-input-wrapper">
                  <input autocapitalize="off" class="field-input" id="MatKhauTaiKhoan" name="entry.1241192792" placeholder="Mật khẩu tài khoản" required="" size="30" onkeyup="this.value=this.value.replace(/[^a-zA-Z0-9*#@]/g,'')" type="text" value="" />
                </div>
                <div class="mota">Mật khẩu tài khoản [Bao gồm chữ thường, chữ HOA, số và 3 kí tự # * @]</div>
              </div>
              <div class="field field-half">
                <div class="field-input-wrapper">
                  <input autocapitalize="off" class="field-input" id="WhatsAppNumber" name="entry.530255908" placeholder="Số điện thoại WhatsApp" required="" pattern="(\+84|0)\d{9,10}" size="30" type="number" value="" />
                </div>
                <div class="mota">Số điện thoại WhatsApp</div>
              </div>
              <div class="field field-half">
                <div class="field-input-wrapper">
                  <input autocapitalize="off" class="field-input" id="SoDienThoai" name="entry.510278204" placeholder="Điện thoại" required="" pattern="(\+84|0)\d{9,10}" size="30" type="number" value="" />
                </div>
                <div class="mota">Số điện thoại</div>
              </div>
<div class="fieldset">
    <div class="field field-third">
      <div class="field-input-wrapper" onchange="AutoUpdateAdress(this)">
      <select class="field-input" id="TinhThanhPhoSelect" aria-label=".form-select-sm">
        <option value="" selected />Chọn tỉnh thành
      </select>
        <div class="mota">Tỉnh / Thành phố</div>
      </div>
    </div>
    <div class="field field-third">
      <div class="field-input-wrapper" onchange="AutoUpdateAdress(this)">
      <select class="field-input" id="QuanHuyenSelect" aria-label=".form-select-sm">
        <option value="" selected />Chọn quận huyện
      </select>
        <div class="mota">Quận / Huyện</div>
      </div>
    </div>
    <div class="field field-third">
    <div class="field-input-wrapper">
      <div class="field-input-wrapper">
      <select class="field-input" id="ward" aria-label=".form-select-sm">
        <option value="" selected />Chọn phường xã
      </select>
        <div class="mota">Phường / Xã</div>
      </div>
    </div>
  </div>
</div>

