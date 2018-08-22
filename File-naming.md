## Nombre de archivos

### 1 Archivos de clase
Los nombres de las clases son escritas en [UpperCamelCase](http://en.wikipedia.org/wiki/CamelCase).

Para clases que extienden de componentes Android, los nombres de las clases deben terminar con el nombre del componente; por ejemplo: `SignInActivity`, `SignInFragment`, `ImageUploaderService`, `ChangePasswordDialog`.

### 2 Archivos de recursos

Los archivos de recursos están escritos en __lowercase_underscore__.

#### 2.1 Archivos Drawable

Nota Al agregar un asset pasarlo primero por ..**********************.. para reducir el tamaño de los mismos.

Convenciones de nombre para drawables:

| Asset Type   | Prefix            |		Example               |
|--------------| ------------------|-----------------------------|
| Action bar   | `ab_`             | `ab_stacked.9.png`          |
| Button       | `btn_`	            | `btn_send_pressed.9.png`    |
| Dialog       | `dialog_`         | `dialog_top.9.png`          |
| Divider      | `divider_`        | `divider_horizontal.9.png`  |
| Icon         | `ic_`	            | `ic_star.png`               |
| Menu         | `menu_	`           | `menu_submenu_bg.9.png`     |
| Notification | `notification_`	| `notification_bg.9.png`     |
| Tabs         | `tab_`            | `tab_pressed.9.png`         |

Convenciones de nombre para iconos (tomado de [Android iconography guidelines](http://developer.android.com/design/style/iconography.html)):

| Asset Type                      | Prefix             | Example                      |
| --------------------------------| ----------------   | ---------------------------- |
| Icons                           | `ic_`              | `ic_star.png`                |
| Launcher icons                  | `ic_launcher`      | `ic_launcher_calendar.png`   |
| Menu icons and Action Bar icons | `ic_menu`          | `ic_menu_archive.png`        |
| Status bar icons                | `ic_stat_notify`   | `ic_stat_notify_msg.png`     |
| Tab icons                       | `ic_tab`           | `ic_tab_recent.png`          |
| Dialog icons                    | `ic_dialog`        | `ic_dialog_info.png`         |

Convenciones de nombre para selector states:

| State	       | Suffix          | Example                     |
|--------------|-----------------|-----------------------------|
| Normal       | `_normal`       | `btn_order_normal.9.png`    |
| Pressed      | `_pressed`      | `btn_order_pressed.9.png`   |
| Focused      | `_focused`      | `btn_order_focused.9.png`   |
| Disabled     | `_disabled`     | `btn_order_disabled.9.png`  |
| Selected     | `_selected`     | `btn_order_selected.9.png`  |


#### 2.2 Archivos de layout

Los archivos de layout, deben coincidir con el nombre de los componentes de Android a los que están destinados, pero moviendo el nombre del componente de nivel superior al principio. Por ejemplo, si estamos creando un diseño para el `SignInActivity`, el nombre del archivo layout debe ser `activity_sign_in.xml`.

| Component        | Class Name             | Layout Name                   |
| ---------------- | ---------------------- | ----------------------------- |
| Activity         | `UserProfileActivity`  | `activity_user_profile.xml`   |
| Fragment         | `SignUpFragment`       | `fragment_sign_up.xml`        |
| Dialog           | `ChangePasswordDialog` | `dialog_change_password.xml`  |
| AdapterView item | ---                    | `item_person.xml`             |
| Partial layout   | ---                    | `partial_stats_bar.xml`       |************************************************************

Un caso ligeramente diferente es cuando estamos creando un diseño que va a ser inflado por un `Adaptador`, por ejemplo, para llenar un` ListView`. En este caso, el nombre del diseño debe comenzar con `item_`.

Tenga en cuenta que hay casos donde estas reglas no serán posibles de aplicar. Por ejemplo, al crear archivos de diseño que están destinados a formar parte de otros diseños. En este caso, debe usar el prefijo `partial_`.

#### 2.3 Archivos de menu

Similar a los archivos de layout, los archivos de menu deben coincidir con el nombre del componente. Por ejemplo, si estamos definiendo un archivo de menu que va a ser usado en el `UserActivity`, entonces el archivo debe ser `activity_user.xml`

Una buena práctica es no incluir la palabra `menu` como parte del nombre porque estos archivos ya están ubicados en el directorio `menu`.

#### 2.4 Archivos en values

Los archivos de recursos en la carpeta values deben estar en __plural__, e.j. `strings.xml`, `styles.xml`, `colors.xml`, `dimens.xml`, `attrs.xml`