# vue3-table-lite

![SampleGif](https://linmasahiro.github.io/vue3-table-lite/sample.gif)

A simple and lightweight data table component for Vue.js 3. Features sorting, paging, row check, dynamic data rendering, supported TypeScript, and more.

## Install
```sh
npm i --save-dev jackmartin-vue3-table-lite
```

## Document and demo

[Document](https://vue3-lite-table.vercel.app/)

[Online Demo](https://vue3-lite-table.vercel.app/simple-examples)

## Support

+ Row check event Support
+ Custom data display Support
+ Pagging Support
+ Sorting Support
+ Custom message Support
+ V-slot Support
+ TypeScript Support
+ Grouping Support

## SampleCode

### import
    import TableLite from "jackmartin-vue3-table-lite";
    import TableLite from "jackmartin-vue3-table-lite/ts"; // TypeScript

## QuickStart
### component
    <table-lite
    :is-loading="table.isLoading"
    :columns="table.columns"
    :rows="table.rows"
    :total="table.totalRecordCount"
    :sortable="table.sortable"
    :messages="table.messages"
    @do-search="doSearch"
    @is-finished="table.isLoading = false"
    />
  ></table-lite>

### data
    const table = reactive({
      isLoading: false,
      columns: [
        {
          label: "ID",
          field: "id",
          width: "3%",
          sortable: true,
          isKey: true,
        },
        {
          label: "Name",
          field: "name",
          width: "10%",
          sortable: true,
        },
        {
          label: "Email",
          field: "email",
          width: "15%",
          sortable: true,
        },
      ],
      rows: [],
      totalRecordCount: 0,
      sortable: {
        order: "id",
        sort: "asc",
      },
    });

### Event
    const doSearch = (offset, limit, order, sort) => {
      table.isLoading = true;

      // Start use axios to get data from Server
      let url = 'https://www.example.com/api/some_endpoint?offset=' + offset + '&limit=' + limit + '&order=' + order + '&sort=' + sort;
      axios.get(url)
      .then((response) => {
        // Point: your response is like it on this example.
        //   {
        //   rows: [{
        //     id: 1,
        //     name: 'jack',
        //     email: 'example@example.com'
        //   },{
        //     id: 2,
        //     name: 'rose',
        //     email: 'example@example.com'
        //   }],
        //   count: 2,
        //   ...something
        // }
        
        // refresh table rows
        table.rows = response.rows;
        table.totalRecordCount = response.count;
        table.sortable.order = order;
        table.sortable.sort = sort;
      });
      // End use axios to get data from Server
    };

## Debug
```ssh
npm i && npm run dev
```

## Build
```sh
npm i && npm run build
```

## More...
[Go to Check!!](https://vue3-lite-table.vercel.app/usage#defMode)