GitHub supports rendering and diffing in a number of non-code file formats.

## [Rendering and diffing images](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#rendering-and-diffing-images)

GitHub can display several common image formats, including PNG, JPG, GIF, PSD, and SVG. In addition to simply displaying them, there are several ways to compare differences between versions of those image formats.

**Note:**

- GitHub does not support comparing the differences between PSD files.
- If you are using the Firefox browser, SVGs on GitHub may not render.

### [Viewing images](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#viewing-images)

You can directly browse and view images in your repository on GitHub.com.

SVGs don't currently support inline scripting or animation.

### [Viewing differences](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#viewing-differences)

You can visually compare images in three different modes: [2-up](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#2-up), [swipe](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#swipe), and [onion skin](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#onion-skin).

#### [2-up](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#2-up)

**2-up** is the default mode; it gives you a quick glimpse of both images. In addition, if the image has changed size between versions, the actual dimension change is displayed. This should make it very apparent when things are resized, such as when assets are upgraded to higher resolutions.

![Screenshot of a diff for an image in 2-up mode. The image on the right is outlined in green and larger than the image on the left, which is outlined in red.](https://docs.github.com/assets/cb-352008/images/help/repository/images-2up-view.png)

#### [Swipe](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#swipe)

**Swipe** lets you view portions of your image side by side. Not sure if colors shifted between different versions? Drag the swipe slider over the area in question and compare the pixels for yourself.

![Screenshot of a diff for an image in swipe mode. A line down the center divides the image into new, outlined in green, and old, outlined in red.](https://docs.github.com/assets/cb-676784/images/help/repository/images-swipe-view.png)

#### [Onion skin](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#onion-skin)

**Onion Skin** really comes in handy when elements move around by small, hard to notice amounts. Did an icon shift two pixels to the left? Drag the opacity slider back a bit and notice if things move around.

## [3D File Viewer](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#3d-file-viewer)

GitHub can host and render 3D files with the _.stl_ extension.

When looking directly at an STL file on GitHub you can:

- Click and drag to spin the model.
- Right click and drag to translate the view.
- Scroll to zoom in and out.
- Click the different view modes to change the view.

### [Fixing slow performance](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#fixing-slow-performance)

If you see

in the corner of the viewer, with the tooltip "WebGL powered hardware support not available," then the WebGL technology is not available on your browser.

WebGL is necessary to take advantage of your computer's hardware to its fullest. We recommend you try browsers like [Chrome](https://www.google.com/intl/en/chrome/browser/) or [Firefox](https://www.mozilla.org/en-US/firefox/new/), which ship with WebGL enabled.

### [Error: "Unable to display"](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#error-unable-to-display)

If your model is invalid, GitHub may not be able to display the file. In addition, files that are larger than 10 MB are too big for GitHub to display.

### [Embedding your model elsewhere](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#embedding-your-model-elsewhere)

To display your 3D file elsewhere on the internet, modify this template and place it on any HTML page that supports JavaScript:

```html
<script src="https://embed.github.com/view/3d/<username>/<repo>/<ref>/<path_to_file>"></script>
```

For example, if your model's URL is [`github.com/skalnik/secret-bear-clip/blob/master/stl/clip.stl`](https://github.com/skalnik/secret-bear-clip/blob/master/stl/clip.stl), your embed code would be:

```html
<script src="https://embed.github.com/view/3d/skalnik/secret-bear-clip/master/stl/clip.stl"></script>
```

By default, the embedded renderer is 420 pixels wide by 620 pixels high, but you can customize the output by passing height and width variables as parameters at the end of the URL, such as `?height=300&width=500`.

**Note**: `ref` can be a branch or the hash to an individual commit (like `2391ae`).

### [Rendering in Markdown](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#rendering-in-markdown)

You can embed ASCII STL syntax directly in Markdown. For more information, see "[Creating diagrams](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams#creating-stl-3d-models)."

## [Rendering CSV and TSV data](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#rendering-csv-and-tsv-data)

GitHub supports rendering tabular data in the form of _.csv_ (comma-separated) and ._tsv_ (tab-separated) files.

![Screenshot of a rendered CSV file, with data shown in a table format.](https://docs.github.com/assets/cb-28294/images/help/repository/rendered-csv.png)

When viewed, any _.csv_ or _.tsv_ file committed to a repository on GitHub.com automatically renders as an interactive table, complete with headers and row numbering. By default, we'll always assume the first row is your header row.

You can link to a particular row by clicking the row number, or select multiple rows by holding down the shift key. Just copy the URL and send it to a friend.

### [Searching data](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#searching-data)

If you want to find a certain value in your dataset, you can start typing in the search bar directly above the file. The rows will filter automatically.

### [Handling errors](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#handling-errors)

Occasionally, you may discover that your CSV or TSV file isn't rendering. In those instances, a message appears above your raw text, suggesting what the error may be.

![Screenshot of a text view of a CSV file. In the header, a message points out an error: "No commas found in this CSV file in line 0."](https://docs.github.com/assets/cb-39868/images/help/repository/csv-render-error.png)

Common errors include:

- Mismatched column counts. You must have the same number of separators in each row, even if the cell is blank
- Exceeding the file size. Our rendering only works for files up to 512KB. Anything bigger than that slows down the browser.
- Using unsupported delimiters, such as semicolons instead of commas.

## [Rendering PDF documents](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#rendering-pdf-documents)

GitHub supports rendering of PDF documents.

Currently, links within PDFs are ignored.

## [Rendering differences in prose documents](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#rendering-differences-in-prose-documents)

Commits and pull requests that include prose documents have the ability to represent those documents with _source_ and _rendered_ views.

The source view shows the raw text that has been typed, while the rendered view shows how that text would look once it's rendered on GitHub. For example, this might be the difference between showing `**bold**` in Markdown, and **bold** in the rendered view.

Prose rendering is supported for rendered documents supported by [github/markup](https://github.com/github/markup):

- Markdown
- AsciiDoc
- Textile
- ReStructuredText
- Rdoc
- Org
- Creole
- MediaWiki
- Pod

To see the changes made to the document as part of a commit, click

.

![Screenshot of the diff for a Markdown file. In the header of the file, a file icon is outlined in dark orange.](https://docs.github.com/assets/cb-35940/images/help/repository/rendered-prose-diff.png)

This "rich diff" highlights the code that has been added and removed.

![Screenshot of the diff for a Markdown file. "@octo-org/core" is struck through, with a red background, followed by "@octocat", with a green background.](https://docs.github.com/assets/cb-29577/images/help/repository/rendered-prose-changes.png)

### [Disabling Markdown rendering](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#disabling-markdown-rendering)

When viewing a Markdown file, you can click **Code** at the top of the file to disable Markdown rendering and view the file's source instead.

![Screenshot of a Markdown file in a GitHub repository showing options for interacting with the file. A button, labeled "Code", is outlined in dark orange.](https://docs.github.com/assets/cb-13772/images/help/writing/display-markdown-as-source-global-nav-update.png)

Disabling Markdown rendering enables you to use source view features, such as line linking, which is not possible when viewing rendered Markdown files.

### [Visualizing attribute changes](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#visualizing-attribute-changes)

We provide a tooltip describing changes to attributes that, unlike words, would not otherwise be visible in the rendered document. For example, if a link URL changes from one website to another, we'd show a tooltip like this:

![Screenshot of the diff for a Markdown file. A tooltip over a link says "href: /octo-org-repo/blob/CONTRIBUTING -> /octo-org/octo-repo/blob/docs/CONTRIBUTING."](https://docs.github.com/assets/cb-36583/images/help/repository/prose-diff-attributes.png)

### [Commenting on changes](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#commenting-on-changes)

[Commit comments](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/commenting-on-a-pull-request) can only be added to files within the _source_ view, on a line-by-line basis.

### [Linking to headers](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#linking-to-headers)

As with [other rendered prose documents](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes), hovering over a header in your document creates a link icon. You can link readers of your rendered prose diff to specific sections.

### [Viewing complex diffs](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#viewing-complex-diffs)

Some pull requests involve a large number of changes with large, complex documents. When the changes take too long to analyze, GitHub can't always produce a rendered view of the changes. If this happens, you'll see an error message when you click the rendered button.

You can still use the source view to analyze and comment on changes.

### [Viewing HTML elements](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#viewing-html-elements)

We don't directly support rendered views of commits to HTML documents. Some formats, such as Markdown, let you embed arbitrary HTML in a document. When these documents are shown on GitHub, some of that embedded HTML can be shown in a preview, while some (like an embedded YouTube video) cannot.

In general, rendered views of changes to a document containing embedded HTML will show changes to the elements that are supported in GitHub's view of the document. Changes to documents containing embedded HTML should always be reviewed in both the rendered and source views for completeness.

## [Mapping GeoJSON/TopoJSON files on GitHub](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#mapping-geojsontopojson-files-on-github)

GitHub supports rendering GeoJSON and TopoJSON map files within GitHub repositories. Commit the file as you would normally using a `.geojson` or `.topojson` extension. Files with a `.json` extension are also supported, but only if `type` is set to `FeatureCollection`, `GeometryCollection`, or `topology`. Then, navigate to the path of the GeoJSON/TopoJSON file on GitHub.

### [Geometry types](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#geometry-types)

Maps on GitHub use [Leaflet.js](http://leafletjs.com) and support all the geometry types outlined in [the geoJSON spec](http://www.geojson.org/geojson-spec.html) (Point, LineString, Polygon, MultiPoint, MultiLineString, MultiPolygon, and GeometryCollection). TopoJSON files should be type "Topology" and adhere to the [TopoJSON spec](https://github.com/mbostock/topojson/wiki/Specification).

### [Embedding your map elsewhere](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#embedding-your-map-elsewhere)

Want to make your GeoJSON map available someplace other than GitHub? Simply modify this template, and place it in any HTML page that supports JavaScript (for example, [GitHub Pages](https://pages.github.com)):

```html
<script src="https://embed.github.com/view/geojson/<username>/<repo>/<ref>/<path_to_file>"></script>
```

For example, if your map's URL is [github.com/benbalter/dc-wifi-social/blob/master/bars.geojson](https://github.com/benbalter/dc-wifi-social/blob/master/bars.geojson), your embed code would be:

```html
<script src="https://embed.github.com/view/geojson/benbalter/dc-wifi-social/master/bars.geojson"></script>
```

By default, the embedded map 420px x 620px, but you can customize the output by passing height and width variables as parameters at the end, such as `?height=300&width=500`.

**Note**: `ref` can be a branch or the hash to an individual commit (like `2391ae`).

### [Mapping in Markdown](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#mapping-in-markdown)

You can embed GeoJSON and TopoJSON directly in Markdown. For more information, see "[Creating diagrams](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams#creating-geojson-and-topojson-maps)."

### [Clustering](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#clustering)

If your map contains a large number of markers (roughly over 750), GitHub will automatically cluster nearby markers at higher zoom levels. Simply click the cluster or zoom in to see individual markers.

### [Something's up with the underlying map](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#somethings-up-with-the-underlying-map)

The underlying map data (street names, roads, etc.) are driven by [OpenStreetMap](http://www.openstreetmap.org/), a collaborative project to create a free editable map of the world. If you notice something's not quite right, since it's open source, simply [sign up](https://www.openstreetmap.org/user/new) and submit a fix.

### [Troubleshooting GeoJSON/TopoJSON files](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#troubleshooting-geojsontopojson-files)

If you're having trouble rendering GeoJSON files, ensure you have a valid GeoJSON file by running it through a [GeoJSON linter](http://geojsonlint.com/). If your points aren't appearing where you'd expect (for example, in the middle of the ocean), it's likely that the data is in a projection which is currently unsupported. Currently, GitHub only supports the `urn:ogc:def:crs:OGC:1.3:CRS84` projection.

Additionally, if your `.geojson` file is especially large (over 10 MB), it is not possible to render within the browser. If that's the case, you'll generally see a message that says we can't show files that large.

It may still be possible to render the data by converting the `.geojson` file to [TopoJSON](https://github.com/mbostock/topojson), a compression format that, in some cases, can reduce filesize by up to 80%. Of course, you can always break the file into smaller chunks (such as by state or by year), and store the data as multiple files within the repository.

### [Further reading about GeoJSON/TopoJSON](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#further-reading-about-geojsontopojson)

- [Azure Maps documentation](https://docs.microsoft.com/en-us/azure/azure-maps/)
- [TopoJSON Wiki](https://github.com/mbostock/topojson/wiki)

## [Working with Jupyter Notebook files on GitHub](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#working-with-jupyter-notebook-files-on-github)

When you add Jupyter Notebook or IPython Notebook files with a _.ipynb_ extension on GitHub.com, they will render as static HTML files in your repository.

The interactive features of the notebook, such as custom JavaScript plots, will not work in your repository on GitHub.com. For an example, see [_Linking and Interactions.ipynb_](https://github.com/bokeh/bokeh-notebooks/blob/main/tutorial/06%20-%20Linking%20and%20Interactions.ipynb).

To view your Jupyter notebook with JavaScript content rendered or to share your notebook files with others you can use [nbviewer](https://nbviewer.jupyter.org/). For an example, see [_Linking and Interactions.ipynb_](https://nbviewer.jupyter.org/github/bokeh/bokeh-notebooks/blob/main/tutorial/06%20-%20Linking%20and%20Interactions.ipynb) rendered on nbviewer.

To view a fully interactive version of your Jupyter Notebook, you can set up a notebook server locally. For more information, see [Jupyter's official documentation](http://jupyter.readthedocs.io/en/latest/index.html).

### [Troubleshooting Jupyter Notebook files](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#troubleshooting-jupyter-notebook-files)

If you're having trouble rendering Jupyter Notebook files in static HTML, you can convert the file locally on the command line by using the [`nbconvert` command](https://github.com/jupyter/nbconvert):

```shell
jupyter nbconvert --to html NOTEBOOK-NAME.ipynb
```

### [Further reading about Jupyter Notebook](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#further-reading-about-jupyter-notebook)

- [Jupyter Notebook's GitHub repository](https://github.com/jupyter/jupyter_notebook)
- [Gallery of Jupyter Notebooks](https://github.com/jupyter/jupyter/wiki)

## [Displaying Mermaid files on GitHub](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#displaying-mermaid-files-on-github)

GitHub supports rendering Mermaid files within repositories. Commit the file as you would normally using a `.mermaid` or `.mmd` extension. Then, navigate to the path of the Mermaid file on GitHub.

For example, if you add a `.mmd` file with the following content to your repository:

```text
graph TD
    A[Friend's Birthday] -->|Get money| B(Go shopping)
    B --> C{Let me think}
    C -->|One| D["Cool <br> Laptop"]
    C -->|Two| E[iPhone]
    C -->|Three| F[fa:fa-car Car]
```

When you view the file in the repository, it is rendered as a flow chart.

![Screenshot of a flow chart. Two arrows point from a box labeled "A" to boxes labeled "B" and "C," and two more arrows point from "B" and "C" to "D."](https://docs.github.com/assets/cb-19340/images/help/repository/mermaid-file-diagram.png)

### [Troubleshooting Mermaid files](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#troubleshooting-mermaid-files)

If your chart does not render at all, verify that it contains valid Mermaid Markdown syntax by checking your chart with the [Mermaid live editor](https://mermaid.live/edit).

If the chart displays, but does not appear as you'd expect, you can create a new [GitHub Community discussion](https://github.com/orgs/community/discussions/categories/general), and add the `Mermaid` label.

#### [Known issues](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#known-issues)

- Sequence diagram charts frequently render with additional padding below the chart, with more padding added as the chart size increases. This is a known issue with the Mermaid library.
- Actor nodes with popover menus do not work as expected within sequence diagram charts. This is due to a discrepancy in how JavaScript events are added to a chart when the Mermaid library's API is used to render a chart.
- Not all charts are a11y compliant. This may affect users who rely on a screen reader.

### [Mermaid in Markdown](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#mermaid-in-markdown)

You can embed Mermaid syntax directly in Markdown. For more information, see "[Creating diagrams](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams#creating-mermaid-diagrams)."

### [Further reading about Mermaid](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#further-reading-about-mermaid)

- [Mermaid.js documentation](https://mermaid-js.github.io/mermaid/#/)
- [Mermaid.js live editor](https://mermaid.live/edit)