# calebsgroub
Repo for calebs code


@inherits LayoutComponentBase

<div class="sidebar">
    <NavMenu />
</div>

<div class="main">
   
    <div class="content px-4 container">
        @Body
    </div>
</div>


///

@import url('open-iconic/font/css/open-iconic-bootstrap.min.css');

html, body {
    font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
}

a, .btn-link {
    color: #0366d6;
}

.btn-primary {
    color: #fff;
    background-color: #1b6ec2;
    border-color: #1861ac;
}

app {
    position: relative;
    display: flex;
    flex-direction: column;
}

.top-row {
    height: 3.5rem;
    display: flex;
    align-items: center;
}

.main {
    flex: 1;
}

    .main .top-row {
        background-color: #f7f7f7;
        border-bottom: 1px solid #d6d5d5;
        justify-content: flex-end;
    }

        .main .top-row > a, .main .top-row .btn-link {
            white-space: nowrap;
            margin-left: 1.5rem;
        }

.main .top-row a:first-child {
    overflow: hidden;
    text-overflow: ellipsis;
}

.sidebar {
    background-image: linear-gradient(180deg, rgb(5, 39, 103) 0%, #3a0647 70%);
}

    .sidebar .top-row {
        background-color: rgba(0,0,0,0.4);
    }

    .sidebar .navbar-brand {
        font-size: 1.1rem;
    }

    .sidebar .oi {
        width: 2rem;
        font-size: 1.1rem;
        vertical-align: text-top;
        top: -2px;
    }

    .sidebar .nav-item {
        font-size: 0.9rem;
        padding-bottom: 0.5rem;
    }

        .sidebar .nav-item:first-of-type {
            padding-top: 1rem;
        }

        .sidebar .nav-item:last-of-type {
            padding-bottom: 1rem;
        }

        .sidebar .nav-item a {
            color: #d7d7d7;
            border-radius: 4px;
            height: 3rem;
            display: flex;
            align-items: center;
            line-height: 3rem;
        }

            .sidebar .nav-item a.active {
                background-color: rgba(255,255,255,0.25);
                color: white;
            }

            .sidebar .nav-item a:hover {
                background-color: rgba(255,255,255,0.1);
                color: white;
            }

.content {
    padding-top: 1.1rem;
}

.navbar-toggler {
    background-color: rgba(255, 255, 255, 0.1);
}

.valid.modified:not([type=checkbox]) {
    outline: 1px solid #26b050;
}

.invalid {
    outline: 1px solid red;
}

.validation-message {
    color: red;
}

#blazor-error-ui {
    background: lightyellow;
    bottom: 0;
    box-shadow: 0 -1px 2px rgba(0, 0, 0, 0.2);
    display: none;
    left: 0;
    padding: 0.6rem 1.25rem 0.7rem 1.25rem;
    position: fixed;
    width: 100%;
    z-index: 1000;
}

#blazor-error-ui .dismiss {
    cursor: pointer;
    position: absolute;
    right: 0.75rem;
    top: 0.5rem;
}

@media (max-width: 767.98px) {
    .main .top-row:not(.auth) {
        display: none;
    }

    .main .top-row.auth {
        justify-content: space-between;
    }

    .main .top-row a, .main .top-row .btn-link {
        margin-left: 0;
    }
}

@media (min-width: 768px) {
    app {
        flex-direction: row;
    }

    .sidebar {
        width: 250px;
        height: 100vh;
        position: sticky;
        top: 0;
    }

    .main .top-row {
        position: sticky;
        top: 0;
    }

    .main > div {
        padding-left: 2rem !important;
        padding-right: 1.5rem !important;
    }

    .navbar-toggler {
        display: none;
    }

    .sidebar .collapse {
        /* Never collapse the sidebar for wide screens */
        display: block;
    }


}

.imageThumbnail {
    height : 200px;
    width : auto;
}

.spinner {
    border: 16px solid silver;
    border-top: 16px solid #337AB7;
    border-radius: 50%;
    width: 80px;
    height: 80px;
    animation: spin 700ms linear infinite;
    top: 40%;
    left: 55%;
    position: absolute;
}

@keyframes spin {

    0% {
        transform: rotate(0deg)
    }


    100% {
        transform: rotate(-360deg)
    }
}

///

using EmployeeManagment.Models;
using Microsoft.AspNetCore.Components;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace EmployeeManagment.Web.Pages
{
    public class EmployeeListBase : ComponentBase
    {


        public IEnumerable<Employee> Employees { get; set; }

        protected override async Task OnInitializedAsync()
        {
            await Task.Run(LoadEmployees);
            
        }

        private void LoadEmployees()
        {
            System.Threading.Thread.Sleep(3000);
            Employee e1 = new Employee
            {

                EmloyeeId = 1,
                FirstName = "john",
                LastName = "Hastinngs",
                Email = "David@pragimtech.com",
                DateOfBirth = new DateTime(1980, 10, 5),
                Gender = Gender.Male,
                Department = new Department { DepartmentId = 1, DeparmentName = "Sarah" },
                PhotoPath = "images/mary.png"

            };


            Employee e2 = new Employee
            {

                EmloyeeId = 2,
                FirstName = "Sam",
                LastName = "Galloway",
                Email = "Sam@pragimtech.com",
                DateOfBirth = new DateTime(1981, 12, 22),
                Gender = Gender.Male,
                Department = new Department { DepartmentId = 1, DeparmentName = "Sarah" },
                PhotoPath = "images/mary.png"

            };

            Employee e3 = new Employee
            {

                EmloyeeId = 3,
                FirstName = "Mary",
                LastName = "Smith",
                Email = "mary@pragimtechcom",
                DateOfBirth = new DateTime(1979, 11, 11),
                Gender = Gender.Female,
                Department = new Department { DepartmentId = 1, DeparmentName = "Sarah" },
                PhotoPath = "images/mary.png"

            };

            Employee e4 = new Employee
            {

                EmloyeeId = 4,
                FirstName = "Sara",
                LastName = "Longway",
                Email = "Sara@pragimtechcom",
                DateOfBirth = new DateTime(1982, 9, 23),
                Gender = Gender.Female,
                Department = new Department { DepartmentId = 1, DeparmentName = "Sarah" },
                PhotoPath = "images/mary.png"

            };

            Employees = new List<Employee> { e1, e2, e3, e4 };




        }



    }
}
///


@page "/"
@inherits EmployeeListBase

<h3>Employee List</h3>

@if(Employees == null)
{
    <div class="spinner"></div>
}

else

{ 

<div class="card-deck">
    @foreach (var employee in Employees)
    {

        <div class="card m-3" style="min-width: 18rem; max-width:30.5%;">
            <div class="card-header">
                <h3>@employee.FirstName @employee.LastName </h3>
            </div>
            <img class="card-img-top imageThumbnail" src="@employee.PhotoPath" />
            <div class="card-footer text-center">
                <a href="#" class="btn btn-primary m-1">View</a>

                <a href="#" class="btn btn-primary m-1">Edit</a>

                <a href="#" class="btn btn-primary m-1">Delete</a>

            </div>
        </div>



    }

</div>
}
///




















