# mac-tunning
Scripts para tunear el Mac

- Desactivar el gatekeeper en Mac

`$ sudo spctl --master-disable`

- Desactivar el gestor de energía de las apps en Mac

`$ defaults write NSGlobalDomain NSAppSleepDisabled -bool YES`

- Mostrar los mensaje de arranque de la BIOS en Mac

  - Activar: `$ sudo nvram boot-args="-v"`
  - Desactivar: `$ sudo nvram boot-args=`

- Teclas de inicio y fin en los teclados extendidos USB en Mac

    - Desde el terminal:
    ```
    $ cd ~/Library
    $ mkdir KeyBindings
    $ cd KeyBindings
    $ nano DefaultKeyBinding.dict
    ```
    - Incluir el texto incluido los bracers:
    ```
    {
    "\UF729" = "moveToBeginningOfLine:"; /* Home */
    "\UF72B" = "moveToEndOfLine:"; /* End */
    "$\UF729" = "moveToBeginningOfLineAndModifySelection:"; /* Shift + Home */
    "$\UF72B" = "moveToEndOfLineAndModifySelection:"; /* Shift + End */
    "^\UF729" = "moveToBeginningOfDocument:"; /* Ctrl + Home */
    "^\UF72B" = "moveToEndOfDocument:"; /* Ctrl + End */
    "$^\UF729" = "moveToBeginningOfDocumentAndModifySelection:"; /* Shift + Ctrl + Home */
    "$^\UF72B" = "moveToEndOfDocumentAndModifySelection:"; /* Shift + Ctrl + End */
    }
    ```
- Ajustar el comportamiento de la exploración de SMB en macOS High Sierra 10.13
  - Fuente: https://support.apple.com/es-es/HT208209
  - Acelerar la exploración en comparticiones de red: 
  `$ defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool TRUE`
  - Forzar al Finder para que recopile primero todos los metadatos: 
  `$ defaults write com.apple.desktopservices UseBareEnumeration -bool FALSE`
  - Desactivar el almacenamiento en caché del directorio: 
  `$ echo "[default]" | sudo tee -a /etc/nsmb.conf echo "dir_cache_off=yes" | sudo tee -a /etc/nsmb.conf`
 
- Refirmar una app de Macbed
  `$ codesign --sign - --force --deep /path/to/app.app`
  
  
