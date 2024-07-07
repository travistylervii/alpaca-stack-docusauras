---
sidebar_position: 2
---

# Members Dashboard

The members dashboard page provides users the ability to access the product / service along with an overview of their account, including personalized content, recent activity, and quick access to key features and settings. 

![Members Dashbaord](/img/members-dashboard.jpg)

## Sidebar 
### Navigation
The routes for the sidebar are controlled in the `/constants/nav-routes.ts` file in the `dashboardNavItems` object.  
Here you will be able to add and remove routes and mark which ones are free and paid members using the `upgrade` boolean.  
![Dashboard Sidebar Routes](/img/dashboard-nav-routes.jpg)

### Sidebar CTA
The sitebar CTA is located in `/components/dashboard/sidebar.tsx`  
![Dashboard Sidebar CTA](/img/dashboard-sidebar-cta.jpg)

