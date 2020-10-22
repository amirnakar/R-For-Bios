# R-For-Bios
This is the ggplot course from Maria Nattestad - here https://github.com/MariaNattestad/R_for_biologists

Lesson 1: first plot, Basic work with R and definitions

Lessons 2-4: Import .csv, exploring the data

Lessons 5: Formatting ggplot

Lessons 6: Plot types

Lessons 7: Faceting and Inset plots

Lessons 8: Heatmaps


Quick references: 

Function quickref

To clear:  CNTRL+L
To move to console: cntrl+2
To move to script    : cntrl+1
Turn things into comments : cntrl+shirt+C


Name	What it does	Syntax	Example	Notes
read.csv: 	Loads data from csv to datafram	dataframe <- read.csv(filename, sep=";", header=FALSE)		Filename here is a variable, with the filename
Names	Changes the headers of dataframe	names(dataframe)[1:4] <- c("V1","V2","V3", "V4")	names(my_data)[1:4] <- c("Height","Weight","Age", "Cat")	
Head	Shows the first few rows of dataframe	head(dataframe)		
Png, tiff, jpeg, pdf	Make a file	png("plotpng.png")		
		
		
Dim	Shows you the size of the data frame in rows, cols	dim(my_data)	> dim(my_data)
[1] 421   9	
Summary	Gives min, max, mean and median	Summary(my_data)		
Mean				
Subset	Filters your data	Subset(dataframe, subset=dataframe$varX=="?")	Validation=subset(my_data, subset=my_data$Validation==1)	
Factor				
Gsub				
Revalue				
class	Tells you if your data is dataframe, vector, matrix etc.	Class(my_data)		


Ggplot quick-ref: 
 
Base = ggplot(my_data,aes(x=chrom,fill=type)) + geom_bar()
Formatting
 
Title	Base  	+ labs(title="Regulatory features by chromosome")
Axis label 	Base 	+ labs(x = "Chromosome",y="Count")
Change Theme	Basic	 + theme_gray
Change Fontsize (global)	Basic	+ theme_gray(base_size = 20)
Change font - global	basic	 + theme_gray(base_size = 12, base_family = "Arial")
Rotate axis text	Base	+ theme(axis.text.x = element_text(angle = 90))
Change font - specific	Base	+ theme(legend.text=element_text(size=20,family="Arial"))
Change Color with pallete 	Basic	 + scale_fill_brewer(palette="YlOrRd")
Change color manually	Basic	+ scale_fill_manual(values = c("green","bisque2","red"))
Change background color	Basic	+ theme(panel.background = element_rect(fill="pink"))
Change gridlines	Basic	+ theme(panel.grid.major = element_line(colour = "blue"),
		                 panel.grid.minor = element_line(colour = "red"))
Remove gridlines	Basic	+ theme(panel.grid.major = element_line(NA),
		             panel.grid.minor = element_line(NA))
Change only X or Y grid	Basic	+ theme(panel.grid.major.y = element_line(size=0.2)
Change tick marks	Basic	+ axis.ticks.x = element_line(color="blue")
Change legend position	Basig	+ theme(legend.position="top") // theme(legend.position=c(1,1)) # top right
Remove legend	Basic	+  guides(fill=FALSE)
Legend title	Base	+ labs(fill="Feature")
To flip X and Y	Base  	+ coord_flip()
Polar coordinated	Base	+ coord_polar()
Scale color gradient	Base	+ scale_colour_gradient(limits=c(0,500))
Remove Legend	Base  	+ guides(fill=FALSE)
Log scale	Base	+ scale_y_log10()
Facet a plot	Base  	+ facet_grid(Gender ~ .)     #Note: Rows ~ Columns

Plot types
Plot	X	Y	Note	Code
Bar plots	Cat	Cat	Y is count	geom_bar()
Histograms	Num	Cat	Y is count	geom_bar()
Scatter plots	Num	Num		geom_point()
Box plots	Cat	Num	Simple distribution	geom_boxplot()
Violin plots	Cat	Num	Detailed distribution	geom_violin()
Density plots	Num	Cat	Y is count (basically like a histogram)	geom_density() 
Dot-plots	Num	Cat	Y is count (basically like a histogram)	 geom_dotplot()
			Each dot is one observation
Line-plots	Num	Num	Connected scatter plot	geom_line()
Pie charts	Num		Not ggplot, use summary statistic	pie(type_counts)
Venn diagrams 	Lists		Not ggplot	venn.diagram()

Heatmap Quickref
Basic syntax: 
	Heatmap(my_matrix)      #Note that it's with a capital H
To modify: 
	Heatmap(my_matrix,…
	
Cluster by column?	cluster_columns=FALSE,
Row name position	row_names_side = "left",
Row dendogram position	row_dend_side = "left",
Row name text size	row_names_gp=gpar(cex=0.4),
Dendogram size	row_dend_width = unit(3, "cm"),
Distance calculation method	clustering_distance_rows ="maximum",
Clusterin method	clustering_method_rows = "ward.D",
Break up into major clusters (visual)	km=2,
Defines the distance between major clusters	gap = unit(1, "cm"),
Annotate the columns	bottom_annotation =HeatmapAnnotation(chromosome_info, col = list(chrom=chromosome.colors),
Legend	show_legend=FALSE)

More mods are here: https://www.rdocumentation.org/packages/ComplexHeatmap/versions/1.10.2/topics/HeatmapAnnotation


