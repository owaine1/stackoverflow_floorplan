# Converting single object to multiple object floorplan
This repo is an explaination (in response to a stackoverflow question) of the stages I would use in converting a single object svg to a multiple object svg.  
I.e.  
Single object svg: only a single object is selectable / manupulatable;  
Multiple object: multiple objects are selectable / manupulatable.  

A  
Create 4 files:  
w_original_floorplan.svg  
x_rough_static_floorplan.svg  
y_rough_live_floorplan.svg  
z_final_floorplan.svg

w_original_floorplan.svg and x_rough_static_floorplan.svg are identical apart from filename.  
y_rough_live_floorplan.svg and z_final_floorplan.svg are empty; to be populated.

Copy x_rough_static_floorplan.svg to y_rough_live_floorplan.svg.  
Open y_rough_live_floorplan.svg on browser using server.

x_rough_static_floorplan.svg find all M and replace with two newlines / symbol M (case sensitive). shift + enter shift + enter /M
___
B  
[this section takes the time]  
Take away 1st '/' in path in y_rough_live_floorplan.svg [shows blackout_floorplan]  
Label x_rough_static_floorplan.svg code section blackout_floorplan where code is.  
(this file is used as rough-work, so being xml / svg valid is irrelevant)

In y_rough_live_floorplan.svg find next '/' and delete it [shows floorplan_top_left_whiteout]  
Label x_rough_static_floorplan.svg code section floorplan_top_left_whiteout where code is.

Have x_rough_static_floorplan.svg and y_rough_live_floorplan.svg open in 2 windows, will be going back and forth to each of them. Keep repeating until at end.

(hint: find tool seems to be on switching from files in vscode, so you can use find / and next one cmd + g easily) Maybe handy to have a paper printout of original svg as reference and label the names of objects you create e.g.bath, sink, table, as you go along (don’t be fooled by this, one table is 'table'. Is 2nd chair chair2, chair_2, chair_two etc.?) etc..
___

C  
Reorder the whole labels and corresponding code in path x_rough_static_floorplan.svg so the labels are ordered next to each other, but in the order they are found in the path:  
e.g.  
…  
table_chairs_1st_c_seat_wo  
table_chairs_whiteout  
table_chairs_3rd_c_seat  
…

Use the 'find' tool here. This process, itself will require a temp file to copy and paste to rather than reorder within the file working on. And rewrite temp to file working on. Might be good idea to create checklist of objects and cross-off as done.
E.g. floorplan, bath, table_chairs, sink…
___
D  
Create path elements from your grouped objects, putting each id as id=“floorplan_main”, id=“bath”, id=“sink” etc.. etc..
___
Bear in mind, the data of how this is drawn is really, really bad. Really they should be drawn with rect elements for a rectangle when possible and a lot of the path data is very unnecessary, but that’s obviously how the application generates the svg.
