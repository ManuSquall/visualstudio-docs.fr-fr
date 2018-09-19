---
title: Débogage en mode mixte pour Python
description: Guide pratique pour déboguer simultanément C++ et Python dans Visual Studio, notamment pour passer d’un environnement à l’autre, afficher les valeurs et évaluer les expressions.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 4d5ec15e6fea377e8ffc23cc5215a88081d0f9bd
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45552082"
---
# <a name="debug-python-and-c-together"></a>Déboguer conjointement Python et C++

La plupart des débogueurs Python standard prend en charge le débogage de code Python uniquement. Toutefois, dans la pratique, Python est utilisé conjointement avec C ou C++ dans les scénarios qui nécessitent de hautes performances ou la possibilité d’appeler les API de plateforme. (Pour la procédure pas à pas, consultez [Créer une extension C++ pour Python](working-with-c-cpp-python-in-visual-studio.md).)

Visual Studio fournit un débogage en mode mixte intégré et simultané pour Python et C/C++ natif si vous avez sélectionné l’option **Outils de développement natifs Python** pour la charge de travail **Développement Python** dans le programme d’installation de Visual Studio.

> [!Note]
> Le débogage en mode mixte n’est pas disponible avec Python Tools pour Visual Studio 1.x dans Visual Studio 2015 et version antérieure.

Les fonctionnalités de débogage en mode mixte sont les suivantes, comme expliqué dans cet article :

- Piles d’appels combinées
- Pas à pas détaillé alternant entre du code Python et natif
- Points d’arrêt dans les deux types de code
- Consultez les représentations Python d’objets dans des cadres natifs et vice versa
- Débogage dans le contexte du projet Python ou du projet C++

![Débogage en mode mixte](media/mixed-mode-debugging.png)

|   |   |
|---|---|
| ![Icône représentant une caméra pour les vidéos](../install/media/video-icon.png "Regarder une vidéo") | Pour introduction des modules C natifs de génération, de test et de débogage avec Visual Studio, visionnez la vidéo [Exploration : créer les modules natifs](https://youtu.be/D9RlT06a1EI) (youtube.com, 9 min09 s). La vidéo s’applique à Visual Studio 2015 et 2017. |

## <a name="enable-mixed-mode-debugging-in-a-python-project"></a>Activer le débogage en mode mixte dans un projet Python

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet Python, sélectionnez **Propriétés**, l’onglet **Déboguer**, puis **Permettre le débogage du code natif**. Cette option active le mode mixte pour toutes les sessions de débogage.

    ![Activation du débogage du code natif](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]
    > Quand vous activez le débogage du code natif, la fenêtre Sortie Python peut disparaître immédiatement à la fin de l’exécution du programme, sans afficher le message de pause habituel **Appuyez sur une touche pour continuer**. Pour forcer une pause, ajoutez l’option `-i` au champ **Exécuter** > **Arguments de l’interpréteur** sous l’onglet **Déboguer** quand vous activez le débogage du code natif. Avec cet argument, l’interpréteur Python passe en mode interactif à la fin du code, où il attend que vous appuyiez sur **Ctrl**+**Z** > **Entrée** pour quitter.

1. Quand vous attachez le débogueur en mode mixte à un processus existant (**Débogage** > **Attacher au processus**), utilisez le bouton **Sélectionner** pour ouvrir la boîte de dialogue **Sélectionner le type de code**. Définissez ensuite l’option **Déboguer ces types de codes**, puis sélectionnez à la fois **Natif** et **Python** dans la liste :

    ![Sélection des types de codes Natif et Python](media/mixed-mode-debugging-code-type.png)

    Les paramètres de type de code sont persistants. Ainsi, si vous souhaitez désactiver le débogage en mode mixte au moment de l’attachement à un autre processus par la suite, désélectionnez le type de code **Python**.

    Vous pouvez sélectionner d’autres types de codes, en plus ou au lieu du type **Natif**. Par exemple, si une application managée héberge CPython, qui utilise lui-même des modules d’extension natifs, et que vous souhaitez les déboguer tous les trois, vous pouvez sélectionner les types **Python**, **Natif** et **Managé** afin de bénéficier d’une expérience de débogage unifiée incluant des piles des appels combinées et l’exécution d’un débogage pas à pas portant sur les trois runtimes simultanément.

1. Quand vous démarrez un débogage en mode mixte pour la première fois, une boîte de dialogue **Symboles Python obligatoires** peut s’afficher (consultez [Symboles pour le débogage en mode mixte](debugging-symbols-for-mixed-mode-c-cpp-python.md)). Vous ne devez installer les symboles qu’une seule fois pour un environnement Python donné. Les symboles sont automatiquement inclus si vous installez la prise en charge de Python par le biais du programme d’installation de Visual Studio 2017.

1. Pour mettre à disposition le code source du code Python standard pendant le débogage, rendez-vous sur [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/), téléchargez l’archive correspondant à votre version, puis extrayez-la dans un dossier. Faites ensuite pointer Visual Studio vers des fichiers spécifiques dans ce dossier quand il vous le demande.

## <a name="enable-mixed-mode-debugging-in-a-cc-project"></a>Activer le débogage en mode mixte dans un projet C/C++

Visual Studio 2017 (version 15.5 et ultérieur) prend en charge le débogage en mode mixte d’un projet C/C++ (par exemple, lors de [l’incorporation de Python dans une autre application, comme décrit sur python.org](https://docs.python.org/3/extending/embedding.html)). Pour activer le débogage en mode mixte, configurez le projet C/C++ pour lancer le **débogage Python/Natif** :

1. Cliquez avec le bouton droit sur le projet C/C++ dans **l’Explorateur de solutions**, puis sélectionnez **Propriétés**.
1. Sélectionnez l’onglet **Débogage**, choisissez **Débogage Python/natif** dans le **Débogueur à lancer**, puis sélectionnez **OK**.

    ![Sélection du débogueur Python/natif dans un projet C/C++](media/mixed-mode-debugging-select-cpp-debugger.png)

Avec cette méthode, sachez que vous ne pouvez pas déboguer le lanceur *py.exe* lui-même, car il génère un processus *python.exe* enfant auquel le débogueur ne sera pas attaché. Si vous souhaitez lancer *python.exe* directement avec des arguments, changez l’option **Commande** dans les propriétés de **débogage de Python/natif** (voir image précédente) pour indiquer le chemin complet vers *python.exe*, puis spécifiez les arguments dans **Arguments de commande**.

### <a name="attaching-the-mixed-mode-debugger"></a>Attachement du débogueur en mode mixte

Pour toutes les versions précédentes de Visual Studio, le débogage en mode mixte direct est activé uniquement lors du lancement d’un projet Python dans Visual Studio, car les projets C/C++ utilisent uniquement le débogueur natif. Vous pouvez toutefois attacher le débogueur séparément :

1. Démarrez le projet C++ sans débogage (**Déboguer** > **Démarrer sans débogage** ou **Ctrl**+**F5**).
1. Sélectionnez **Déboguer** > **Attacher au processus**. Dans la boîte de dialogue qui s’affiche, sélectionnez le processus approprié, puis utilisez le bouton **Sélectionner** pour ouvrir la boîte de dialogue **Sélectionner le type de code**. Dans celle-ci, sélectionnez **Python** :

    ![Sélection de Python comme type de débogage au moment de l’attachement d’un débogueur](media/mixed-mode-debugging-attach-type.png)

1. Sélectionnez **OK** pour fermer cette boîte de dialogue, puis sélectionnez **Attacher** pour démarrer le débogueur.
1. Vous devrez peut-être introduire une pause ou un délai approprié dans l’application C++ pour que celle-ci n’appelle pas le code Python à déboguer avant que vous n’ayez la possibilité d’attacher le débogueur.

## <a name="mixed-mode-specific-features"></a>Fonctionnalités spécifiques du mode mixte

- [Pile des appels combinée](#combined-call-stack)
- [Pas à pas détaillé alternant entre du code Python et natif](#step-between-python-and-native-code)
- [Vue des valeurs PyObject dans le code natif](#pyobject-values-view-in-native-code)
- [Vue des valeurs natives dans le code Python](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Pile des appels combinée

La fenêtre **Pile des appels** affiche des frames de pile natifs et Python entrelacés, en insérant des transitions entre les deux :

![Pile des appels combinée](media/mixed-mode-debugging-call-stack.png)

Si l’option **Outils** > **Options** > **Débogage** > **Général** > **Activer Uniquement mon code** est définie, les transitions apparaissent sous la forme **[Code externe]**, sans spécifier la direction de la transition.

Un double-clic sur un frame d’appel quelconque active ce dernier et ouvre le code source approprié, si cela est possible. Si le code source n’est pas disponible, le frame est quand même activé et les variables locales peuvent être inspectées.

### <a name="step-between-python-and-native-code"></a>Pas à pas détaillé alternant entre du code Python et natif

Quand vous utilisez les commandes **Pas à pas détaillé** (**F11**) ou **Pas à pas sortant**  (**Maj**+**F11**), le débogueur en mode mixte gère correctement l’alternance entre ces types de codes. Par exemple, lorsque Python appelle une méthode d’un type implémenté en C, le pas à pas détaillé sur un appel de cette méthode s’arrête au début de la fonction native implémentant la méthode. De même, lorsqu’un code natif appelle une fonction API Python, un code Python est appelé. Par exemple, l’exécution d’un pas à pas détaillé dans `PyObject_CallObject` sur une valeur de fonction initialement définie dans Python s’arrête au début de la fonction Python. L’exécution d’un pas à pas détaillé alternant entre un code Python et natif est également prise en charge pour les fonctions natives appelées à partir de Python par le biais de [ctypes](https://docs.python.org/3/library/ctypes.html).

### <a name="pyobject-values-view-in-native-code"></a>Vue des valeurs PyObject dans le code natif

Quand un frame natif (C ou C++) est actif, ses variables locales s’affichent dans la fenêtre **Variables locales** du débogueur. Dans les modules d’extension Python natifs, de nombreuses variables sont de type `PyObject` (qui est un typedef de `_object`), ou de quelques autres types Python fondamentaux (consultez la liste ci-dessous). Dans le cadre du débogage en mode mixte, ces valeurs présentent un nœud enfant supplémentaire intitulé **[Vue Python]**. Quand ce nœud est développé, il affiche la représentation Python de la variable, telle qu’elle apparaîtrait si une variable locale référençant le même objet était présente dans un frame Python. Les enfants de ce nœud sont modifiables.

![Vue Python](media/mixed-mode-debugging-python-view.png)

Pour désactiver cette fonctionnalité, cliquez avec le bouton droit sur un emplacement quelconque de la fenêtre **Variables locales**, puis désélectionnez l’option de menu **Python** > **Afficher les nœuds de la vue Python** :

![Activation de la vue Python](media/mixed-mode-debugging-enable-python-view.png)

Types C affichant les nœuds **[Vue Python]** (si cette option est activée) :

- `PyObject`
- `PyVarObject`
- `PyTypeObject`
- `PyByteArrayObject`
- `PyBytesObject`
- `PyTupleObject`
- `PyListObject`
- `PyDictObject`
- `PySetObject`
- `PyIntObject`
- `PyLongObject`
- `PyFloatObject`
- `PyStringObject`
- `PyUnicodeObject`

**[Vue Python]** n’apparaît pas automatiquement pour les types que vous créez vous-même. Quand vous créez des extensions pour Python 3.x, ceci n’est généralement pas un problème, car tout objet comporte au final un champ `ob_base` de l’un des types ci-dessus, ce qui entraîne l’apparition des nœuds **Vue Python**.

Toutefois, pour Python 2.x, chaque type d’objet déclare généralement son en-tête sous la forme d’une collection de champs inline, et il n’existe aucune association entre les types créés personnalisés et `PyObject` au niveau du système de type en code C/C++. Pour activer les nœuds **[Vue Python]** pour de tels types personnalisés, modifiez le fichier *PythonDkm.natvis* dans le [répertoire d’installation de Python Tools](installing-python-support-in-visual-studio.md#install-locations), et ajoutez un autre élément dans le code XML pour votre struct C ou classe C++.

Une autre option (mieux adaptée) consiste à suivre la spécification [PEP 3123](https://www.python.org/dev/peps/pep-3123/) et à utiliser un champ `PyObject ob_base;` explicite plutôt que `PyObject_HEAD`, bien que cette opération ne soit pas toujours possible pour des raisons de compatibilité descendante.

### <a name="native-values-view-in-python-code"></a>Vue des valeurs natives dans le code Python

Comme dans la section précédente, vous pouvez activer un nœud **[C++ view]** (Vue C++) pour les valeurs natives dans la fenêtre **Variables locales** quand un frame Python est actif. Cette fonctionnalité est désactivée par défaut. Si vous souhaitez l’activer, cliquez avec le bouton droit dans la fenêtre **Variables locales**, puis sélectionnez l’option **Python** > **Afficher les nœuds de la vue C++**.

![Activation de la vue C++](media/mixed-mode-debugging-enable-cpp-view.png)

Le nœud **[Vue C++]** fournit une représentation de la structure C/C++ sous-jacente d’une valeur, telle qu’elle apparaîtrait dans un frame natif. Par exemple, il affiche une instance de `_longobject` (dont `PyLongObject` est un typedef) pour un entier long Python, et il essaie de déduire les types des classes natives que vous avez vous-même créées. Les enfants de ce nœud sont modifiables.

![Vue C++](media/mixed-mode-debugging-cpp-view.png)

Si un champ enfant d’un objet est du type `PyObject` ou de l’un des autres types pris en charge, il comporte un nœud de représentation **[Vue Python]** (si ces représentations sont activées), ce qui offre la possibilité de parcourir les graphiques d’objet quand les liens ne sont pas directement exposés à Python.

Contrairement aux nœuds **[Vue Python]**, qui utilisent les métadonnées d’objet Python pour déterminer le type de l’objet, il n’existe aucun mécanisme suffisamment fiable pour **[C++ view]** (Vue C++). En règle générale, pour une valeur Python donnée (autrement dit, une référence `PyObject`) il est impossible de déterminer avec certitude la structure C/C++ sous-jacente. Le débogueur en mode mixte tente de déduire ce type en examinant les différents champs du type de l’objet (comme l’élément `PyTypeObject` référencé par son champ `ob_type`) qui comportent des types de pointeur fonction. Si l’un de ces pointeurs fonction référence une fonction qui peut être résolue, et que cette fonction comporte un paramètre `self` avec un type plus spécifique que `PyObject*`, ce type est considéré comme le type de stockage. Par exemple, si l’élément `ob_type->tp_init` d’un objet donné pointe vers la fonction suivante :

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

le débogueur peut correctement en déduire que le type C de l’objet est `FobObject`. S’il ne parvient pas à déterminer un type plus précis en fonction de `tp_init`, il passe aux autres champs. S’il lui est impossible de déduire le type d’après l’ensemble de ces champs, le nœud **[C++ view]** (Vue C++) présente l’objet sous la forme d’une instance `PyObject`.

Pour obtenir systématiquement une représentation utile pour les types créés personnalisés, il est préférable d’inscrire au moins une fonction spéciale lors de l’inscription du type et d’utiliser un paramètre `self` fortement typé. La plupart des types répondent automatiquement à cette exigence ; dans le cas contraire, `tp_init` constitue généralement l’entrée la plus simple à utiliser dans ce but. Une implémentation factice de `tp_init` pour un type servant uniquement à permettre la déduction du type de débogueur peut simplement renvoyer immédiatement la valeur zéro, comme dans l’exemple de code ci-dessus.

## <a name="differences-from-standard-python-debugging"></a>Différences par rapport au débogage Python standard

Le débogueur en mode mixte se différencie du [débogueur Python standard](debugging-python-in-visual-studio.md) par le fait qu’il offre certaines fonctionnalités supplémentaires, tout en étant dépourvu de certaines capacités associées à Python :

- Fonctionnalités non prises en charge : points d’arrêt conditionnels, fenêtre de **débogage interactive** et débogage à distance multiplateforme.
- Fenêtre **Exécution** : disponible mais avec un sous-ensemble de fonctionnalités restreint, incluant notamment toutes les limitations répertoriées dans cette section.
- Versions Python prises en charge : CPython 2.7, 3.3 et versions ultérieures uniquement.
- Visual Studio Shell : lorsque vous utilisez Python avec Visual Studio Shell (par exemple, si vous l’avez installé à l’aide du programme d’installation intégré), Visual Studio n’est pas en mesure d’ouvrir les projets C++, et l’expérience de modification des fichiers C++ se limite à celle d’un éditeur de texte de base. Toutefois, le débogage C/C++ et le débogage en mode mixte sont entièrement pris en charge dans Shell avec le code source, l’exécution d’un pas à pas détaillé dans le code natif et l’évaluation des expressions C++ dans les fenêtres de débogage.
- Visualisation et développement d’objets : quand vous visualisez des objets Python dans les fenêtres d’outil de débogage **Variables locales** et **Espion**, le débogueur en mode mixte présente uniquement la structure des objets. Il n’évalue pas automatiquement les propriétés et n’affiche pas les attributs calculés. Dans le cas des collections, il présente uniquement les éléments pour les types de collections intégrés (`tuple`, `list`, `dict`, `set`). Les types de collections personnalisés ne sont pas visualisés sous forme de collections, sauf s’ils sont hérités d’un type de collection intégré.
- Évaluation des expressions : voir ci-dessous.

### <a name="expression-evaluation"></a>Évaluation des expressions

Le débogueur Python standard autorise l’évaluation des expressions Python arbitraires dans les fenêtres **Espion** et **Exécution** quand le processus débogué est suspendu au niveau d’un emplacement quelconque dans le code, à condition qu’il ne soit pas bloqué dans une opération d’E/S ou dans un autre appel système similaire. Dans le cadre du débogage en mode mixte, les expressions arbitraires ne peuvent être évaluées qu’en cas d’arrêt dans le code Python, après un point d’arrêt ou lors d’un pas à pas détaillé dans le code. Les expressions ne peuvent être évaluées que sur le thread sur lequel le point d’arrêt ou l’opération pas à pas se sont produits.

Lors d’un arrêt dans le code natif, ou dans le code Python lorsque les conditions ci-dessus ne s’appliquent pas (par exemple, après une opération de pas à pas sortant, ou sur un autre thread), l’évaluation des expressions se limite à accéder aux variables locales et globales dans la portée du frame actuellement sélectionné, à accéder aux champs de ces variables et à indexer les types de collections intégrés avec des littéraux. Par exemple, l’expression ci-après peut être évaluée dans n’importe quel contexte (à condition que tous les identificateurs référencent des variables existantes et des champs des types appropriés) :

```python
foo.bar[0].baz['key']
```

Le débogueur en mode mixte résout également de telles expressions d’une autre manière. Toutes les opérations d’accès aux membres recherchent uniquement les champs qui font directement partie intégrante de l’objet (tels qu’une entrée dans ses éléments `__dict__` ou `__slots__`, ou un champ d’un struct natif exposé à Python par le biais de `tp_members`), et ignorent tout élément `__getattr__`, `__getattribute__` ou toute logique de descripteur. De même, toutes les opérations d’indexation ignorent `__getitem__` et accèdent directement aux structures de données internes des collections.

Par souci de cohérence, ce schéma de résolution de noms est utilisé pour toutes les expressions qui correspondent aux contraintes relatives à l’évaluation des expressions limitée, que les expressions arbitraires soient ou non autorisées au niveau du point d’arrêt actuel. Pour imposer la sémantique Python appropriée lorsqu’un évaluateur complet est disponible, indiquez l’expression entre parenthèses :

```python
(foo.bar[0].baz['key'])
```
