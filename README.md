#Copy-files-from-multiple-subfolders-to-a-single-folder-with-the-subfolder-name-attached-to-their-fil
Copy files from multiple subfolders to a single folder with the subfolder name attached to their filenames

#Create new folder to move all files into
new_dir <- "/Users/jobinvarughese/Desktop/For Ravi"
dir.create(new_dir)

old_names <- list.files("/Users/jobinvarughese/Desktop/For Ravi/Palni_copy", 
                        recursive=TRUE, full.names = T)
old_names

# Rename files by reordering elements and replacing slashes
# with underscores
new_names <- gsub(
  pattern = "^(.*)/(.*)/(.*)/(.*)/(.*)/(.*)/(.*)/(.*)$",
  replacement = "\\1_\\2_\\3_\\4_\\5_\\6_\\7_\\8",
  x = old_names)
new_names
#> [1] "Palni_BGO872_2_uc_export=download_id=1zxiVjI0_K1wjC_426rgBR4grv4dWVIeO.jpg_bel50"  

file.copy(from=old_names, to=paste0(new_dir, "/", new_names), overwrite = T)
#> [1] TRUE

