# `Story`

---

### Зачем нам stories?

---

Когда мы разрабатываем приложение, мы зачастую хотим его паралелльно отлаживать от банальных ошибок (особоенно фронт), а вставлять элементы в index.tsx мы не хотим. И тут у нас появляется StoryBook, он умеет:

-   В **real time** показывать изменения отдельного компонента
-   Структурировать наши компоненты

> P.S плюс без сторис вас буду пинать сначала я, а потом Никита, так что да...

### Как мы работаем со stories?

---

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

---

-   Правилом хорошего тона является создание файла **NameOfComponent.usecase.tsx**,
    куда выносится подстановка значений в props
-   Больше при работе вряд ли понадобится, если же вдруг такое происходит, можете написать @ADmiOK или почитать документацию.
