<template>
  <div class="home">
    <!-- <pro-form :columns="autoData.columns" v-model="autoData.value"></pro-form> -->
    <Button @click="click">aaa</Button>
    <pro-table
      :request="request"
      :map="map"
      :toolBar="toolBar"
      :columns="columns"
      :submitForm="submitForm"
      :search="{ searchLineNum: 2 }"
      :format="format"
    >
    </pro-table>

    <!-- <pro-table :columns="columns" :searchLineNum="5"> </pro-table> -->
  </div>
</template>

<script>
// import axios from "axios";
import dayjs from "dayjs";
export default {
  name: "Home",
  data() {
    return {
      toolBar: true,
      autoData: {
        columns: [
          {
            title: "标题",
            key: "toolBar",

            type: "radio"
          }
        ],
        value: {
          toolBar: false
        }
      },
      format: {
        // formatCurrent({ page }) {
        //   const { current, pageSize } = page;
        //   return { ...page, current: (current - 1) * pageSize };
        // }
        formatCurrent: "(page.current - 1) * page.pageSize"
      },
      columns: [
        {
          title: "cataLog",
          group: "B",
          key: "cataLog",
          renderSearch: {
            type: "Radio"
          },
          renderForm: {
            type: "DatePicker",
            props: {
              placeholder: "lastDate",
              format: "yyyy-MM-dd hh:mm:ss"
            },
            format(value) {
              return dayjs(value).format("YYYY-MM-DD hh:mm:ss");
            }
          },
          renderTable: () => {
            return (
              <Button
                onclick={() => {
                  console.log("aaa");
                }}
              >
                aaa
              </Button>
            );
          }
        },
        {
          title: "createUser",
          rules: {
            required: true
          },
          key: "createUser",
          renderSearch: () => {
            return <div>aaa</div>;
          }
        },
        {
          title: "form",
          key: "form"
        },
        {
          title: "createUser3",
          key: "createUser2"
        },
        {
          title: "createUser3",
          key: "createUser3"
        },
        {
          title: "createUser4",
          key: "createUser4"
        },
        {
          title: "createUs3er4",
          key: "createUs3er4"
        },
        {
          title: "descript",
          tooltip: true,
          tooltipMaxWidth: 700,
          key: "descript"
        },
        {
          title: "操作",
          key: "action",
          actions: [
            {
              title: "编辑",
              method: "POST",
              type: "edit",
              request: "https://yapi.ihotel.cn/mock/67/sys/sysOptionList"
              // request(options) {
              //   console.log(options);
              //   return axios.post(
              //     "https://yapi.ihotel.cn/mock/67/sys/sysOptionList",
              //     {
              //       a: options.row.cateLog
              //     }
              //   );
              // }
            },
            {
              type: "delete",
              title: "删除",
              request: "http://127.0.0.1:7068/api/v1/users/1",
              method: "DELETE"
            }
            // {
            //   title: "删除",
            //   type: "delete",
            //   // method: "delete",
            //   // request: "/id",
            //   keys: ["id"]
            // }
          ]
        }
      ],
      request: "https://yapi.ihotel.cn/mock/106/api/table",
      // request(options) {
      //   console.log(options);
      //   return axios.get("https://yapi.ihotel.cn/mock/67/sys/sysOptionList", {
      //     params: { ...options }
      //   });
      // },
      map: {
        dataPath: "data",
        totalPath: "totalRows"
      },
      submitForm: "https://yapi.ihotel.cn/mock/67/sys/sysOptionList"
    };
  },
  methods: {
    click() {
      this.toolBar = false;
    },
    table() {
      const ref = this.$refs.proSearch;
      console.log(ref.value);
    }
  }
};
</script>
<style>
.home {
  width: 70%;
  margin: 0 auto;
}
</style>
