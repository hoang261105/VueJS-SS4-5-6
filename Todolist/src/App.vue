<template>
  <section class="vh-100 gradient-custom">
    <div class="container py-5 h-100">
      <div class="row d-flex justify-content-center align-items-center h-100">
        <div class="col col-xl-10">
          <div class="card">
            <div class="card-body p-5">
              <form
                class="d-flex justify-content-center align-items-center mb-4"
              >
                <div class="form-outline flex-fill">
                  <input
                    type="text"
                    id="form2"
                    class="form-control"
                    v-model="inputValue"
                  />
                  <label class="form-label" for="form2"
                    >Nhập tên công việc</label
                  >
                </div>
                <button
                  type="submit"
                  class="btn btn-info ms-2"
                  @click="handleAdd"
                >
                  Thêm
                </button>
              </form>

              <!-- Tabs navs -->
              <ul class="nav nav-tabs mb-4 pb-2">
                <li class="nav-item" role="presentation">
                  <a class="nav-link active">Tất cả</a>
                </li>
                <li class="nav-item" role="presentation">
                  <a class="nav-link">Đã hoàn thành</a>
                </li>
                <li class="nav-item" role="presentation">
                  <a class="nav-link">Chưa hoàn thành</a>
                </li>
              </ul>
              <!-- Tabs navs -->

              <!-- Tabs content -->
              <div class="tab-content" id="ex1-content">
                <div class="tab-pane fade show active">
                  <ul
                    class="list-group mb-0"
                    v-for="job in listItem"
                    :key="job.id"
                  >
                    <li
                      class="list-group-item d-flex align-items-center justify-content-between border-0 mb-2 rounded"
                      style="background-color: #f4f6f7"
                    >
                      <div>
                        <input
                          class="form-check-input me-2"
                          type="checkbox"
                          :checked="job.status"
                          @change="handleUpdate(job.id)"
                        />
                        <span
                          :style="{
                            textDecoration: job.status
                              ? 'line-through'
                              : 'none',
                          }"
                          >{{ job.name }}</span
                        >
                      </div>
                      <div class="d-flex gap-3">
                        <i class="fas fa-pen-to-square text-warning"></i>
                        <i
                          class="far fa-trash-can text-danger"
                          @click="handleDelete(job.id)"
                        ></i>
                      </div>
                    </li>
                  </ul>
                </div>
              </div>

              <div>
                <p>
                  Tổng số công việc hoàn thành:
                  <b>{{ completeJob }}/{{ listItem.length }}</b>
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive, ref, watch, watchEffect } from "vue";
const inputValue = ref("");
const listItem = reactive(JSON.parse(localStorage.getItem("listJob")) || []);
const completeJob = ref(0);

const saveData = (key, value) => {
  localStorage.setItem(key, JSON.stringify(value));
};

const handleAdd = () => {
  // Validate dữ liệu
  if (!inputValue.value) {
    alert("Tên công việc không được để trống");
    return;
  }

  // Hàm kiểm tra trùng tên
  const findJob = listItem.find((item) => item.name === inputValue.value);

  if (findJob) {
    alert(`Tên công việc ${inputValue.value} đã tồn tại`);
    return;
  }
  console.log(findJob);

  listItem.push({
    id: Math.ceil(Math.random() * 10000),
    name: inputValue,
    status: false,
  });

  saveData("listJob", listItem);

  inputValue.value = "";
};

const handleUpdate = (id) => {
  const findIndex = listItem.findIndex((item) => item.id === id);
  if (findIndex !== -1) {
    listItem[findIndex].status = !listItem[findIndex].status;
    saveData("listJob", listItem);
  }
};

const handleDelete = (id) => {
  const confirmDelete = confirm("Bạn có chắc chắn muốn xóa không?");
  if (confirmDelete) {
    const filterJob = listItem.filter((item) => item.id !== id);
    // Cập nhật lại listJob
    listItem.length = 0;
    listItem.push(...filterJob);
    saveData("listJob", listItem);
  }
};

const updateStatusJob = () => {
  // Lọc ra những công việc có status = true
  const filterJobCompleted = listItem.filter((item) => item.status);

  // Cập nhật lại giá trị cho biến completed job
  completeJob.value = filterJobCompleted.length;
};

// Trong Vue thì sử dụng use watch để lắng nghe sự thay đổi của 1 biến
watch(listItem, () => {
  updateStatusJob();
});
</script>

<style>
.gradient-custom {
  background: radial-gradient(50% 123.47% at 50% 50%, #00ff94 0%, #720059 100%),
    linear-gradient(121.28deg, #669600 0%, #ff0000 100%),
    linear-gradient(360deg, #0029ff 0%, #8fff00 100%),
    radial-gradient(100% 164.72% at 100% 100%, #6100ff 0%, #00ff57 100%),
    radial-gradient(100% 148.07% at 0% 0%, #fff500 0%, #51d500 100%);
  background-blend-mode: screen, color-dodge, overlay, difference, normal;
}

i {
  cursor: pointer;
}

.overlay {
  position: fixed;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
}

.modal-custom {
  background-color: #fff;
  padding: 20px 24px;
  height: 170px;
  width: 400px;
  margin-top: 100px;
  border-radius: 4px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.modal-header-custom {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.modal-footer-footer {
  display: flex;
  justify-content: flex-end;
  gap: 8px;
}
</style>
