# Makefile for ocvdemo
#
#   Copyright 2015 J.A. / http://www.tsdconseil.fr
#
#   Project web page: http://www.tsdconseil.fr/log/opencv/demo/index-en.html
#
#   This file is part of OCVDemo.
#
#   OCVDemo is free software: you can redistribute it and/or modify
#   it under the terms of the GNU Lesser General Public License as published by
#   the Free Software Foundation, either version 3 of the License, or
#   (at your option) any later version.
#
#   OCVDemo is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU Lesser General Public License for more details.
#
#   You should have received a copy of the GNU Lesser General Public License
#   along with OCVDemo.  If not, see <http://www.gnu.org/licenses/>.

# Project name
PROJECT= ocvdemo

# Path to repository root directy
RPATH = ..

# Definition of individual files to compiled
# Yes, this is the right place to add your new demonstration source file name.
SOURCES_BASE= image-selecteur photographie image-mosaic filtrage morpho-demo gradient-demo reco-demo histo seuillage video-demo espaces-de-couleurs 3d boutils-image demos-registration gestion-souris ocvdemo-mmi ocvdemo-export demo-skeleton misc segmentation

# (Optionnal) Sources requiring a graphic toolkit -> will not be included in the reduced library
SOURCES_IHM=

# (Optionnal) Executable targets to be build (each one must have an associated source file)
EXECS:= ocvdemo test-webcam

# (Optionnal) Special directories to locate the source files
# (not counting ./src and ./include)
ADDITIONNAL_SRC_DIRS = src/tools src/demo-items

# Version of the OpenCV demonstrator
# Révision du démonstrateur OpenCV 
VMAJ   = 1
VMIN   = 1
VPATCH = 0

# Version of the OpenCV library
# Révision de la librairie OpenCV
OCV_VMAJ   = 3
OCV_VMIN   = 0
OCV_VPATCH = 0

CDEFS =  -DOCV_VMAJ=$(OCV_VMAJ) -DOCV_VMIN=$(OCV_VMIN) -DOCV_VPATCH=$(OCV_VPATCH)
CDEFS += -DVMAJ=$(VMAJ) -DVMIN=$(VMIN) -DVPATCH=$(VPATCH)
ADDITIONNAL_INC_DIRS= $(CDEFS) -I ../ocvext/include -I$(RPATH)/libcutil/include -I$(RPATH)/libdsp/include

ifeq ($(OCVIPATH),)
 # OCVIPATH not defined, assume that OpenCV is installed in default directories (e.g. /usr/include/, etc.)
else
 # OCVIPATH is defined: it should be the path where opencv was builded
ADDITIONNAL_INC_DIRS += -I$(OCVIPATH)
ADDITIONNAL_LOPT     += -L$(OCVLPATH)
endif

ifeq ($(TARGET),LINUX)
else
ADDITIONNAL_INC_DIRS +=  -march=i486
endif


# External libraries
EXTERNAL_LIBS = $(RPATH)/libcutil

# (Optionnal) Additionnal targets to be build after library and executables
ADDITIONNAL_TARGETS =

FIRST_TARGETS =

ifeq ($(TARGET),LINUX)
ADDITIONNAL_LOPT += ../ocvext/build/ocvext.lib -lopencv_core -lopencv_highgui -lopencv_objdetect -lopencv_features2d -lopencv_stitching -lopencv_imgproc -lopencv_imgcodecs -lopencv_videoio -lopencv_video -lopencv_calib3d -lopencv_photo
else
ADDITIONNAL_LOPT += ../ocvext/build/ocvext.lib -mwindows
ADDITIONNAL_LOPT += -lopencv_core300 -lopencv_imgproc300 -lopencv_highgui300 -lopencv_video300 -lopencv_videoio300 -lopencv_features2d300 -lopencv_objdetect300 -lopencv_imgcodecs300 -lopencv_calib3d300 -lopencv_stitching300 -lopencv_photo300 -march=i486
#-lfftw3-3 -lfftw3f-3 
endif

ADDITIONNAL_CLEAN =

# Common definitions for Makefiles and build rules
include $(RPATH)/libcutil/data/std-makefile-defs
