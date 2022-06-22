# Reorienting 4D NIfTI files

This repository contains a bash script for swapping and flipping the axes of a 4D NIfTI file, such as an fMRI timeseries. 

## Dependencies

This script requires [ANTs](https://github.com/ANTsX/ANTs) and [Convert3D](http://www.itksnap.org/pmwiki/pmwiki.php?n=Convert3D.Doc2) to run.

- ANTs installation instructions can be found [here](https://github.com/ANTsX/ANTs) (scroll down the README).
- Convert3D installation instructions can be found [here](http://www.itksnap.org/pmwiki/pmwiki.php?n=Downloads.C3D).

## Running the Script

Useful note: you can view the header of a 4D NIfTI with the `PrintHeader` ANTs command.

Things to edit in the script to make it suite your needs:
- input variable: the path to the input 4D NIfTI
- time_spacing variable: the time spacing in the 4D NIfTI (4th entry of the spacing list in the NIfTI header) 
- time_origin variable: the time origin in the 4D NIfTI (4th entry of the origin list in the NIfTI header)
- output variable: the path for the output 4D NIfTI
- new_orientation variable: the desired anatomical orientation for the NIfTI volumes (such as RAS)

## How the script works

The script disassembles the input 4D NIfTI into its component 3D NIfTIs using ANTs ImageMath. The script then loops through these component 3D NIfTIs and reorients each 3D NIfTI to the desired orientation using Convert3D. The component 3D NIfTIs are finaly reassembled into the output 4D NIfTI using ANTs ImageMath.
