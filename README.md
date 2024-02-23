# Calcasieu Parish Soccer Club Website

This repository hosts the content for the Calcasieu Soccer Club.
It is currently hosted at calcasieusoccerclub.netlify.app and is under construction. The existing site exists at http://cscsoccerclub.org

## Updating the Site

Below are the instructions for how to make simple changes to the website. They can generally be done by just having
a GitHub account and modifying the files in the browser. You can always download/edit/upload new files but it is slightly more
complicated because it requires using the command-line.

### Modifying an Existing Page

If you are simply trying to change text on a page, navigate to the file (on Github). Content pages are found in the
`content` directory and then in subfolders depending on the page you're editing.

Once you get to the page, on the upper-right there is a button for "Edit this page". Click it, make the changes, then
in the upper right there is another button `Commit changes...`. It will bring up a popup about "commit messages" and a few
other things. These are just details that will show up in the "History" of the file; they are not vital exactly but providing
a meaningful message will help you understand in the future why you were making certain changes. You just have to click `Commit changes` and you're done!

### Adding or Removing New Pages

If  you want to add a new web page, you need to generally add a new folder as well (notice the structure of how you go to `programs -> eagles -> index.md`, so you have multiple folders then one file). You can do this also from the web interface.

In the upper right, click on `Add file`. There is a textbox for content of the file but also above it is a textbox where you'll
add the file name. To create the folder, just type in `folderYouWant/fileNameYouWant` and the folder is automatically made as necessary.

Its easiest to just start from another file that is similar to what you want. Copy/paste that file's text into the page described above (add file, type folder/file names, paste content into the larger box). Then just click "Commit" and finish up the commit description as described in the "Modifying an existing page" section above.

### Adding or Removing Options on the Landing Page

These buttons are described in the `content/_index/hero.md` file. Just edit that file as desired. Each button is described in a
section like

```
[[buttons]]
  text = "Programs"
  url = "/programs"
  color = "warning"
```

The text/URL are pretty self explanitory but the color refers to a list of colors in the `config.toml` (https://github.com/johnSchnake/csc/blob/main/config.toml#L115)

### Adding or Removing Options on the Menu or Footer

Navigate to the `config.toml` page and scroll down/search for the sections labeled `menu.footer` (for the footer) or `menu.main` (for the header). Just copy/paste one of those sections that look like:

```
[[menu.footer]]
  url = "/programs"
  name = "Programs"
  weight = 10
```

Then you'll want to edit those values:
 - weight determines what order they get listed in
 - name is what will be printed on the page
 - URL will determine where it goes when you click it. If you dont have `http://` as a prefix, it will be a URL relative to your website. This is why `/programs` links to `<your website>/programs`

### Changing Colors or Minor Visuals

This does generally require more expertise but many people do feel comfortable making some HTML/CSS changes. If this doesn't apply to you, just reach out to me or another developer who can guide the change.

If you feel so inclined to proceed, you can edit the `static/css/custom.css` file. This contains CSS for small things I customized on the site.

You can play with changes here to see how it impacts things. You can also just view the website, right click on the element on the page you want to change, and click on `Inspect`. It will open a toolbar in your browser and describe how the HTML/CSS is generated. You can edit those to play quickly with small changes. Then go back to the `custom.css` file and change it as necessary.

### Changing Pictures

This requires two steps (both can be done in the web interface):
 1. Adding the image itself
 2. Referencing the image

To upload the file, go to the `static/images` folder (not `content` this time). Then in the upper right, click `Add file...` then `Upload file`. You can commit that change as described earlier in this page.

To reference the image, navigate to the file responsible for the web page where that image lives (e.g. the `content/programs/eagles/index.md` file). Now you just need to edit that file and refer to the new image. Most often the reference is near the top such
as:

```
[asset]
  image = "eaglesItem.jpg"
```

Notice you don't need to refer to the full path of the image (`static/images/eaglesItem.jpg`). Just the base name is fine and it knows where to find those images.

If there is some other way in which the image is embedded in the page, it is probably just a variant of this: find where the old image is named, update the name to the new images name.

Optionally you can delete that older, unused image now but it is not necessary.

### Adding/Removing Advertiser Logos

This is partially similar to the section above for changing images. You'll need to upload the image but instead of `static/images` you'll add it into `static/images/ads`.

After that, you need to add it to the list of advertisers. The file that lists these is `config.toml`. If you scroll down
there is a section with entries like this:

```
  [params.ads]
    [params.ads.ad01]
      image = "ads/bradberry.jpg"
      url = "https://www.imperialhealth.com/services/family-medicine/"
      tier = "tier1"
```

If you need to remove an advertiser, just delete that entry.

If you need to add one, edit this page (see the section on modifying pages above) and copy/paste one of these `params.ads.ad01` sections (not the higher level `[params.ads]` line). Then you just update the image to say the newly uploaded ad image. Update the URL to link to the advertiser's homepage (or wherever you want). Then edit the tier to be either `tier1` `tier2` or `tier3`. The tier 1 advertisers get larger images than tier 3.

**Note: it doesn't matter what you name the ad; it just has to be unique. That's why they are currently just listed as `ad01` `add12` etc. **

### Limitations

In general, modifying the site in the ways listed above are very easy and do not require much expertise.
Some changes however would potentially require more developer experience.
Listed below are some cases which, although possible, would likely require developer experience:

 - Changing the number of buttons for programs
 - Changing the general look and feel of the site in non-trivial ways

## TODO

 - [x] adjust buttons in list to be vertically aligned on the side? Already centered so maybe ok.
 - [x] Fill in copy from existing site
 - [x] Advertiser logos (new ones)
 - [x] Alternate background color for items in list
 - [x] Pictures for all the programs?
 - [x] Simple way to make announcements?
 - [ ] New Pictures
 - [ ] New advertisers
 - [x] Finish resources page
 - [x] Write "How-To" doc

Copyright 2017 - The Syna Theme Starter Authors

