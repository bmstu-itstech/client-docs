____
# **`Работа с React компонентами`**
____
### Что такое Component и с чем его едят?
______
    Основной конструкционной единицей в React считается Component.
Компонентом является функция, возвращающая JSX элемент, который в последствии явно пригодится использовать еще раз, или же который явно можно отделить от другой части сайта, не потеряв целостности самого сайта.

#### Важно:
_____
Всё что __не связано__ напрямую с текущим контекстом __ДОЛЖНО БЫТЬ__ выделено в отдельный компонент.

###### *Пример:*
____
В компоненте __Header__ нельзя располагать __Home__, __About__ и тп ссылки, т.к. компонент заголовка никак не связан с текстом Home, About, все ссылки и текст __ДОЛЖНЫ__ быть вынесены в аргументы.
>Допускается иметь компонент, MainHeader, который использует компонент навигация как layout и передаёт в него наши ссылки.
Которые желательно должны находится в какой-то сущности типа ПутиНавигации

### Расположение компонентов
____
    Под компоненты следует выделять отдельную папку components.
    Каждый компонент также в свою очередь является папкой, состоящий из:

• Component.tsx самого компонента
• Component.props.tsx компонента (об этом позже)
• файл Component.styles.css / Component.styles.sass / Component.styles.scss, любой другой PostCss (при необходимости)

 ###### *Пример:*
 ____
- src
    - components
        - Button   
            - Button.props.tsx
            - Button.tsx
        - Card
            - Card.tsx
            - Card.props.tsx
        - Header
            - Header.tsx
            - Header.props.tsx

#### Важно:
___
>Компоненты, как и файлы этих компонентов, следует называть с большой буквы.
Пример:
-   Назначение компонента: Кнопка в обычном дефолтном варианте
-   Название папки компонента: Button
-   Название файла компонента: Button.tsx
-   Название файла пропсов компонента: Button.props.tsx
-   Название файл стилей компонентов: Button.styles.css
****
# **`Issue`**
****
### Порядок работы над задачей:
____
|Перетащил issue в “in progress”| Открыл pull request  >|Команда сделала ревью|
|:-:|:-:|:-:|
|v| ^ |v|
|__Решил issue >__| __Перетащил в “in review”__|__Перетащил в “done”__|

#### Важно:
-----
>•	При открытии PR ставим в __assignee__ того, __кто выполнил таску__ (то есть ты сам)
•	Название PR сохраняет стиль нейминга как у коммитов в ветках
 (т.е. part_of_code type_of_commit: what_was_done )
 
# `Про разработку`


* не рекомендую писать css, он будет в большом объёме мной браковаться, точнее отправляться на исправление
* если вы считаете, что вы не бог css, то не реккомендую его использовать
>переходите на tailwind ❤️
__________________________
* Обязательно пишите сторис на любые компоненты, если сторис нет, то компонент также отправляется на исправление


__________________________
* Используйте линтер, как минимум пока-что форматтер,

# `Story`
____
### Зачем нам stories?
_____
Когда мы разрабатываем приложение, мы зачастую хотим его паралелльно отлаживать от банальных ошибок (особоенно фронт), а вставлять элементы в index.tsx мы не хотим. И тут у нас появляется StoryBook, он умеет:
- В __real time__ показывать изменения отдельного компонента
- Структурировать наши компоненты

> P.S плюс без сторис вас буду пинать сначала я, а потом Никита, так что да...


### Как мы работаем со stories?
____
берем, копируем шаблон
```javascript
import {Meta, StoryObj} from "@storybook/react";
import NameOfCcomponent from "@/components/NameOfCcomponent/index";
import Props from "./NameOfCcomponent.props";
import ImportedDefaultUseCaseFromFile from './NameOfCcomponent.usecase.tsx'

const meta: Meta<Props> = {
    component: NameOfCcomponent,
}

export default meta;

type Story = StoryObj<Props>;

export const Default: Story = {
    args: {
        // здесь все props из Props принимают свои значения
        title: 'Я Такой молодей, вы бы знали',
        description: 'ГООООООЛ'
        
        или же 
        
        ...ImportedDefaultUseCaseFromFile
    },
}
// здесь можно написаь еще шаблонов
export const NameOfStoryInStoryBook: Story = {
    args: {
        // здесь все props из Props принимают свои значения
        ...ImportedUseCaseFromFile
    },
}

```
### Важно
_____
- Правилом хорошего тона является создание файла __NameOfComponent.usecase.tsx__,
куда выносится подстановка значений в props
- Больше при работе вряд ли понадобится, если же вдруг такое происходит, можете написать @ADmiOK или почитать документацию.

# `Git`
____
### Нейминг коммитов / веток
____
##### Важно:
____
•	Универсального нейминга коммитов и веток нет, не было и вряд ли будет
•	Придя на новое рабочее место, вы скорее всего увидите что-то новое

На данный момент в нашей организации правильный нейминг такой:

 - __Ветки:__
 ____
__НАЗВАНИЕ_ПРОЕКТА-номер_задачи_которую_решает_ветка__
>Номер задачи можно найти в календарике задач

##### Важно:
____
> Каждая ветка – отдельная задача

###### *Пример:*
____
	__RS-5678__ 
	__REG-322__

- __Коммиты:__

###### *Пример:*
____
__handlers feat: implement ActionHandler__
###### Здесь:
	__handlers__ - это какой-то раздел проекта
	__feat__ - тип коммита, например fix, feat (новая фича), test, ref (refactoring), del и т.д.(все типы можно найти в статье раздела ‘Полезное’)
	__implement ActionHandler__ – что было сделано (кратко)


__Полезное__:
Angular Commit Format Reference Sheet (https://gist.github.com/brianclements/841ea7bffdb01346392c)
