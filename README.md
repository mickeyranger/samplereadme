# samplereadme
# react-datatable-report

This is datatable view in React.js

##About
It is about view table data or report structure view, for data in react js


##Features

It currently supports:

1. Humanized column names based on object keys
1. Sortable columns
1. Search term highlight in the results
1. Column visibility toggles
1. Automatic pagination
1. Smart data rendering
   - URLs and E-Mail addresses rendered as the _href_ in an _anchor_ tag
     `<a />`
   - _boolean_ value parsing to yes/no word
   - Image URLs rendered as the _src_ for an image tag `<img />`
1. Custom override if the default behavior is unwanted for some columns
1. Control the order of the columns


## Installation

```sh

npm install react-datatable-report

```


## Context


You can find the example with sample code and descriptions,



```jsx
import React from "react";
import { FaMoneyBillAlt } from "react-icons/fa";
import ReportTable from  "react-report-datatable-component";
export default function SampleReport() {
    const data = [
        {
            "employee_name": "employee name 1",
            "salary": 200,
            "gross_salary": 100,
            "net_salary": 100,
        },
        {
            "employee_name": "employee name 2",
            "salary": 200,
            "gross_salary": 100,
            "net_salary": 100,
        },
        {
            "employee_name": "employee name 3",
            "salary": 200,
            "gross_salary": 100,
            "net_salary": 100,
        },
        {
            "employee_name": "employee name 4",
            "salary": 200,
            "gross_salary": 100,
            "net_salary": 100,
        },
    ]
    const columns = [
        {
            Header: 'S.No.',
            accessor: (row, index) => index + 1,
            Footer: '',
            align: 'right',
            width: 20
        },
        {
            Header: 'Employee Name',
            accessor: 'employee_name',
            Footer: 'Total',
            align: 'left',
            width: 20
        },
        {
            Header: 'Salary Details',
            columns: [
                {
                    Header: 'Gross Salary',
                    accessor: 'gross_salary',
                    Footer: data?.reduce((a, v) => a = a + v.gross_salary, 0),
                    align: 'right',
                    Cell: ({ value }) => (<><FaMoneyBillAlt style={{ fontSize: "16px", color: "green" }} /> <span>{value}</span></>), width: 120
                },
                {
                    Header: 'Net Salary',
                    accessor: 'net_salary',
                    Footer: data?.reduce((a, v) => a = a + v.net_salary, 0),
                    align: 'right',
                    width: 150
                },
            ],
            headerAlign: "center"
        },
        {
            Header: 'Salary',
            accessor: 'salary',
            Footer: data?.reduce((a, v) => a = a + v.salary, 0),
            align: 'right',
            width: 70
        },
    ];
    return (<div>
		<ReportDataTable columns={columns} data={data} keyField="S.No" pagination={true} exportfilename={"sampledata"}
                exportspecificheaders={true} exportheaders={true} exportspecifictheme={true} />
</div>)
}  
	

```


## Props

| Name               		| Default               | Type                  | Description                                                       			|
| :------------------------ | :-------------------- | :-------------------- | :---------------------------------------------------------------------------- |
| data              		| []                    | {array}   			| An array of plain objects          						        			|
| keyField           		| 'data'                | {string}              | The Unique Key Field for order rowdata                            			|
| columns		     		| []                	| {array}            	| Columns or Table Header to view the data, complex headers also allowed      	|
| pagination		 		| false                 | {boolean}             | Pagination of the table with default 10 rows per Page    						|
| exportfilename     		| false                 | {boolean}             | Filename for exported one, which is excel or pdf								|
| exportspecificheaders 	| false                 | {boolean}             | Dynamically export , columns which are required in export option            	|
| exportheaders         	| false                 | {boolean}             | Export option for data in two format i.e., excel and pdf          			|
| exportspecifictheme   	| false                 | {boolean}             | To enable theme to display table different style format                       |
