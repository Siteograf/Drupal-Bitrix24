# Drupal Bitrix24

You should edit this module for you tasks.
I used in form Bootstrap 4 classes.

![Drupal Bitrix24 ](/screenShot.png)

### Russian description
Выкладываю его в качестве примера.
Модуль создает блок с формой и отпраляет данные в Bitrix24 и там создается лид.

Настройки принимает с полей. В модулей они не задаются

``` php
$fastorder_crm_host = variable_get('fastorder_crm_host');
$fastorder_crm_login = variable_get('fastorder_crm_login');
$fastorder_crm_password = variable_get('fastorder_crm_password');
```

Если нужно дополните модуль настройками.
Я использовал для этого другой самодельный модуль fastorder.
Там были такие поля для настройки:

``` php
function fastorder_form_alter(&$form, &$form_state, $form_id)
{
    if ($form_id == 'system_site_information_settings') {
        $form['crm_bitrix24'] = array(
            '#type' => 'fieldset',
            '#title' => t('CRM Bitrix24'),
            '#weight' => -1,
            '#collapsible' => FALSE,
            '#collapsed' => FALSE,
        );

        $form['crm_bitrix24']['fastorder_crm_host'] = array(
            '#type' => 'textfield',
            '#title' => t('CRM HOST'),
            '#default_value' => variable_get('fastorder_crm_host', '.bitrix24.ru'),
            '#weight' => 1,
        );

        $form['crm_bitrix24']['fastorder_crm_login'] = array(
            '#type' => 'textfield',
            '#title' => t('CRM login'),
            '#default_value' => variable_get('fastorder_crm_login', ''),
            '#weight' => 2,
        );

        $form['crm_bitrix24']['fastorder_crm_password'] = array(
            '#type' => 'textfield',
            '#title' => t('CRM password'),
            '#default_value' => variable_get('fastorder_crm_password', ''),
            '#weight' => 3,
        );

        $form['crm_bitrix24']['fastorder_crm_sousrceid'] = array(
            '#type' => 'textfield',
            '#title' => t('CRM Source ID'),
            '#default_value' => variable_get('fastorder_crm_sousrceid', ''),
            '#weight' => 4,
        );
    }

    $form['#submit'][] = 'fastorder_system_site_information_settings_form_submit';
}
```

### CSS
В полях есть placeholder. Можно дописать себе так

```css
.labelHidden label {
    display: none;
}
```
или убрать плейсхолдеры:
```php
'#attributes' => array(
    'placeholder' => 'Ваше имя',
),
```

Если этот модуль актуален пишите на info@siteograf.com помогу с адаптацией

