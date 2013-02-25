# Kolors

Uses KMeans clustering and the L*A*B* colorspace to extract "approximate human vision" dominant colors from an image.  Optionally, map those dominant colors into preferred "color bins" for a search index facet-by-color solution.

LARGELY based off the neat work of the [Miro gem](https://github.com/jonbuda/miro).  If you want faster, RGB-based dominant color extraction, use Miro.

## Dependencies

Requires Imagemagick.  On OSX use homebrew to install: brew install imagemagick

## Installation

$ gem install kolors

## Usage

```ruby
require 'kolors'

# Use path to a local image or URL for remote image
kolors = Kolors::DominantColors.new('../colors/images/QFZMF57HPHVGJ8Z_thumb.png')

# Two methods for color retrieval
# 1) KMeans-based clustered color analysis
# 2) Non-clustered, color pixel count percentages (more colors here)

# KMeans - Return the dominant colors in LAB
kolors.to_lab
 => [[52.406, -18.186, 27.618], [88.523, -10.393, 16.203], [64.944, -16.181, 24.419], [28.486, -16.665, 22.73]]

# KMeans - Return the mapped color bins and color percentage for facet-by-color
kolors.to_facets
 => [{"Moss"=>50.05952380952381}, {"Mercury"=>9.880952380952381}, {"Aluminum"=>19.186507936507937}, {"Iron"=>20.873015873015873}]
 
kolors.to_lab # LAB values
kolors.to_rgb # RGB values
 
# Non-clustered - Color pixel count percentages
kolors.color_bins_result
 => [{"Moss"=>31.785714285714285}, {"Asparagus"=>22.658730158730158}, {"Aluminum"=>7.420634920634921}, {"Tungsten"=>5.396825396825397}, {"Magnesium"=>4.821428571428572}, {"Iron"=>4.424603174603175}, {"Steel"=>4.067460317460317}, {"Silver"=>3.8293650793650795}, {"Tin"=>3.7896825396825395}, {"Mercury"=>3.6904761904761907}, {"Nickel"=>3.5515873015873014}, {"Lead"=>2.380952380952381}, {"Snow"=>2.0634920634920633}, {"Licorice"=>0.11904761904761905}]
 
```

## TODOS

1. Simplify configuration of "color bins" for facet-by-color mapping

## Thanks

Special thanks to my buddy [Nate Vack](https://github.com/njvack) for help getting this off of the ground.

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
