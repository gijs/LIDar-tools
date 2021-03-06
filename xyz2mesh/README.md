# Install Dependences

## Install cmake, Boost, GMP and MPFR

```brew install boost gmp mpfr```

## Install Eigen

1. Download [Eigen source code](http://eigen.tuxfamily.org/index.php?title=Main_Page)

```wget http://bitbucket.org/eigen/eigen/get/3.2.2.tar.gz```

2. Un Zip it

```tar xzvf 3.2.2.tar.gz```

3. Move the subdirectory ```Eigen/``` to your ```/usr/local/include```

```
cd eigen-eigen-*
mv Eigen /usr/local/include/
```

## Install CGAL

You can just do:

```brew install cgal```

or 

1. Download [CGAL source code](http://www.cgal.org/)

```wget https://gforge.inria.fr/frs/download.php/file/34149/CGAL-4.5.tar.gz```

2. Un zip it

```tar xzvf CGAL-4.5.tar.gz```

3. Compile

```
cd CGAL-4.5 # go to CGAL directory
cmake . # configure CGAL
make # build the CGAL libraries
```

4. Install

```make install```

#  Compile xyz2mesh

```
cd LIDar-tools/xyz2mesh/
cgal_create_CMakeLists -s xyz2mesh 
cmake -DCGAL_DIR=/usr/local/include/CGAL . # Double check this!!
make
```

# Use

```
Usage: ./xyz2mesh file_in.xyz file_out.off [options]

PointCloud **simplification** options:
  -cell_size <float>          Size of the cell for the simplification (default=0.5)

PointCloud **outliers removal**:
  -rm_nb_neighbors <float>    Nearby Neighbors for Outliers Removal (default=24)
  -rm_percentage <float>      Percentage of outliers to remove (default=0)

PointCloud **normal estimation**:
  -nb_neighbors <float>       Nearby Neighbors for Normal Estimation (default=100)

Surface **poisson reconstruction**:
  -solver <string>            Linear solver name (default=)
  -sm_angle <float>           Min triangle angle (default=20 degrees)
  -sm_radius <float>          Max triangle size w.r.t. point set average spacing (default=100)
  -sm_distance <float>        Approximation error w.r.t. point set average spacing (default=0.25)
  -approx <float>             Approximation ratio (default=0.02)
  -ratio <float>              Average spacing ratio (default=5)
```