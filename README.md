
# vocabjava_flatpak
Vocabulary Builder 1.33 by  Amit Shrestha rorokimdim https://github.com/rorokimdim

Java based flatpak, Vocabulary Builder for GRE

![](https://github.com/fastrizwaan/vocabjava_flatpak/blob/main/screenshots/1.png)

#### install flathub repo and freedesktop sdk 20.08
```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install flathub org.freedesktop.Sdk/x86_64/20.08 runtime/org.freedesktop.Sdk.Extension.openjdk11/x86_64/20.08
```

#### clone and build flatpak from yaml
```
git clone https://github.com/fastrizwaan/vocabjava_flatpak.git
cd vocabjava_flatpak

# build
flatpak-builder --force-clean build-dir io.github.vocabjava.yaml

# install 
flatpak-builder --user --install --force-clean build-dir io.github.vocabjava.yaml

# run
flatpak run io.github.vocabjava
```

#### Build a flatpak bundle file from the above built repo:
```
flatpak-builder --repo="repo" --force-clean "build" io.github.vocabjava.yaml
flatpak --user remote-add --no-gpg-verify "vocabjava" "repo"
flatpak build-bundle "repo" "vocabjava.flatpak" io.github.vocabjava  --runtime-repo="https://flathub.org/repo/flathub.flatpakrepo"

flatpak --user install vocabjava.flatpak
flatpak run io.github.vocabjava
```

