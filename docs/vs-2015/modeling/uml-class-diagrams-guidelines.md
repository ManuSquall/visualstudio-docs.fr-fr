---
title: 'Diagrammes de classes UML : Indications | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.overrideoperationsdialog
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: 94dbfd55-b300-4b49-9049-0831ed849486
caps.latest.revision: 56
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: cba454162cb9116dc1d2946a5c136b377354d7d7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852178"
---
# <a name="uml-class-diagrams-guidelines"></a>Diagrammes de classes UML : indications
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, vous pouvez utiliser un *diagramme de classes UML* pour décrire les types de données et leurs relations, indépendamment de leur implémentation. Le diagramme permet de se concentrer sur les aspects logiques des classes, plutôt que sur leur implémentation.  
  
 Pour créer un diagramme de classes UML, sur le **Architecture** menu, choisissez **nouveau diagramme UML ou diagramme de couche**.  
  
 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Prise en charge des versions pour les outils d'architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!NOTE]
>  Cette rubrique concerne les diagrammes de classes UML. Il existe un autre genre de diagramme de classes, que vous pouvez créer et utiliser pour visualiser le code du programme. Consultez [conception et affichage des Classes et des Types](http://go.microsoft.com/fwlink/?LinkId=142231).  
  
##  <a name="Using"></a> À l’aide de diagrammes de classes UML  
 Vous pouvez utiliser un diagramme de classes UML à diverses fins :  
  
-   Pour fournir une description indépendante de l'implémentation des types utilisés dans un système et passés entre ses composants.  
  
     Par exemple, le type Commande de repas peut être implémenté dans le code .NET de la couche métier, dans le XML au niveau des interfaces entre les différents composants, dans les bases de données SQL, ainsi que dans l'interface utilisateur du HTML. Bien que ces implémentations diffèrent dans les détails, la relation entre Commande de repas et les autres types, tels que Menu et Paiement, est toujours la même. Le diagramme de classes UML permet d'évoquer ces relations indépendamment des implémentations.  
  
-   Pour clarifier le glossaire des termes utilisés pour la communication entre l'application et ses utilisateurs, ainsi que dans les descriptions de leurs besoins. Consultez [modéliser les besoins des utilisateurs](../modeling/model-user-requirements.md).  
  
     Par exemple, considérez les descriptions des récits utilisateur, des cas d’usage ou des autres exigences d’une application de restaurant. Dans une telle description, vous recherchez des termes tels que Menu, Commande, Repas, Prix, Paiement, etc. Vous pouvez dessiner un diagramme de classes UML qui définit les relations entre ces termes. Cela réduira le risque d'incohérences dans les descriptions d'impératifs, dans l'interface utilisateur et dans les documents d'aide.  
  
### <a name="relationship-to-other-diagrams"></a>Relation aux autres diagrammes  
 Un diagramme de classes UML est généralement dessiné avec d'autres diagrammes de modélisation, afin de fournir des descriptions des types qu'ils utilisent. En tous les cas, la représentation physique des types n'est pas impliquée par l'un des diagrammes.  
  
 Diagramme d'activités  
  
 Type des données traversant un nœud d'objet.  
  
 Types de broches d'entrée et de sortie, et de nœuds de paramètres d'activités.  
  
 Consultez [diagrammes d’activités UML : instructions](../modeling/uml-activity-diagrams-guidelines.md).  
  
 Diagramme de séquence  
  
 Types de paramètres et de valeurs de retour de messages.  
  
 Types des lignes de vie. La classe d'une ligne de vie doit inclure des opérations pour tous les messages qu'elle peut recevoir.  
  
 Consultez [diagrammes de séquence UML : indications](../modeling/uml-sequence-diagrams-guidelines.md).  
  
 Diagramme de composant  
  
 Interfaces de composant, répertoriant leurs opérations.  
  
 Consultez [diagrammes de composants UML : indications](../modeling/uml-component-diagrams-guidelines.md).  
  
 Diagramme de cas d'usage  
  
 Types mentionnés dans les descriptions des objectifs et des étapes d'un cas d'usage.  
  
 Consultez [diagrammes de cas d’usage UML : indications](../modeling/uml-use-case-diagrams-guidelines.md).  
  
##  <a name="BasicSteps"></a> Étapes de base pour dessiner des diagrammes de classe  
 Pour plus d’informations de référence sur les éléments des diagrammes de classes UML, consultez [diagrammes de classes UML : référence](../modeling/uml-class-diagrams-reference.md).  
  
> [!NOTE]
>  Les étapes détaillées pour créer un des diagrammes de modélisation sont décrites dans [modèles et diagrammes UML modifier](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-uml-class-diagram"></a>Pour créer un diagramme de classes UML  
  
1.  Sur le **Architecture** menu, choisissez **nouveau UML ou diagramme de couche**.  
  
2.  Sous **modèles**, choisissez **diagramme de classes UML**.  
  
3.  Nommez le diagramme.  
  
4.  Dans **ajouter au projet de modélisation**, sélectionnez un projet de modélisation existant dans votre solution, ou **créer un nouveau projet de modélisation**, puis choisissez **OK**.  
  
     Un nouveau diagramme de classes apparaît avec la **UMLClass diagramme** boîte à outils. La boîte à outils contient les relations et les éléments requis.  
  
#### <a name="to-draw-a-uml-class-diagram"></a>Pour dessiner un diagramme de classes UML  
  
1.  Pour créer un type, choisissez le **classe**, **Interface** ou **énumération** outil sur la boîte à outils, puis cliquez sur une partie vide du diagramme. (Si vous ne voyez pas la Boîte à Outils, appuyez sur Ctrl+Alt+X.)  
  
2.  Pour ajouter des attributs ou des opérations pour les types ou les littéraux à une énumération, choisissez le **attributs**, **opérations** ou **littéraux** du titre dans le type, et appuyez sur ENTRÉE.  
  
     Vous pouvez écrire une signature telle que `f(x:Boolean):Integer`. Consultez [attributs et opérations](#AttributesAndOperations).  
  
     Pour ajouter plusieurs éléments rapidement, appuyez deux fois sur ENTRÉE à la fin de chaque élément. Vous pouvez utiliser les touches de direction pour vous déplacer vers le haut ou le bas de la liste.  
  
3.  Pour développer ou réduire un type, choisissez l’icône de chevron située en haut à gauche de celui-ci. Vous pouvez également développer et réduire les **attributs** et **opérations** section d’une classe ou interface.  
  
4.  Pour dessiner des liens d'associations, d'héritage ou encore de dépendance entre les différents types, cliquez successivement sur l'outil approprié, sur le type source et sur le type cible.  
  
5.  Pour créer des types dans un package, créez un package à l’aide de la **Package** outil, puis créez-y des types et des packages au sein du package. Vous pouvez également utiliser la commande de copie pour copier des types et les coller dans un package.  
  
6.  Un diagramme est une vue dans un modèle partagé entre les autres diagrammes du même projet. Pour afficher une arborescence complète du modèle, choisissez **vue**, **Windows autres**, **Explorateur de modèles UML**.  
  
##  <a name="UsingTypes"></a> À l’aide des Classes, Interfaces et énumérations  
 Il existe trois genres standard de classifieurs disponibles dans la boîte à outils. Ils sont désignés comme *types* tout au long de ce document.  
  
 ![Une classe, une énumération et une interface](../modeling/media/uml-classguidetypes.png "UML_ClassGuideTypes")  
  
- Utilisez **Classes** (1) pour représenter les types de données ou un objet pour la plupart des cas.  
  
- Utilisez **Interfaces** (2) dans un contexte où vous avez à faire la distinction entre les interfaces pures et les classes concrètes qui disposent d’implémentations internes. Cette différence est utile lorsque l'objectif du diagramme consiste à décrire une implémentation logicielle. Celle-ci est moins utile lorsque vous modélisez des données passives ou que vous définissez des concepts permettant de décrire les besoins des utilisateurs.  
  
- Utilisez un **énumération** (3) pour représenter un type qui a un nombre limité de valeurs littérales, par exemple `Stop` et `Go`.  
  
  -   Ajoutez les valeurs littérales à l'énumération. Attribuez à chacune un nom bien distinct.  
  
  -   Si vous le souhaitez, vous pouvez également fournir une valeur numérique pour chaque valeur littérale. Ouvrez le menu contextuel pour le littéral dans l’énumération, choisissez **propriétés**, puis tapez un nombre dans le **valeur** champ dans le **propriétés** fenêtre.  
  
  Attribuez un nom unique à chaque type.  
  
### <a name="getting-types-from-other-diagrams"></a>Obtention de types d'autres diagrammes  
 Vous pouvez faire apparaître des types d'un autre diagramme dans votre diagramme de classes UML.  
  
 Diagramme de classes UML  
  
 Vous pouvez faire apparaître une classe sur plusieurs diagrammes de classes UML. Lorsque vous avez créé une classe dans un diagramme, faites-la glisser depuis **Explorateur de modèles UML** vers l’autre diagramme.  
  
 Cette opération est utile si vous souhaitez que chaque diagramme se concentre sur un groupe particulier de relations.  
  
 Par exemple, vous pourriez afficher les associations entre une Commande de repas et le Menu de restaurant dans un diagramme, de même que celles entre Commande de repas et Paiement, dans un autre.  
  
 Diagramme de composant  
  
 Si vous avez défini des interfaces sur les composants dans un diagramme de composant, vous pouvez faire glisser une interface à partir de **Explorateur de modèles UML** sur le diagramme de classes. Dans le diagramme de classes, vous pouvez définir des méthodes incluses dans l'interface.  
  
 Consultez [diagrammes de composants UML : indications](../modeling/uml-component-diagrams-guidelines.md).  
  
 Diagramme de séquence UML  
  
 Vous pouvez créer des classes et des interfaces à partir de lignes de vie dans un diagramme de séquence et puis faites glisser la classe à partir de **Explorateur de modèles UML** vers un diagramme de classes UML. Chaque ligne de vie d'un diagramme de séquences représente une instance d'objet, de composant ou encore d'acteur.  
  
 Pour créer une classe à partir d’une ligne de vie, ouvrez le menu contextuel pour la ligne de vie, puis choisissez **créer une classe** ou **créer l’Interface**. Consultez [diagrammes de séquence UML : indications](../modeling/uml-sequence-diagrams-guidelines.md).  
  
##  <a name="AttributesAndOperations"></a> Attributs et opérations  
 Un attribut (4) est une valeur nommée que chaque instance de type peut posséder. L'accès à un attribut ne modifie pas l'état de l'instance.  
  
 Une opération (5) est une méthode ou une fonction que les instances du type peuvent exécuter. Elle peut retourner une valeur. Si son **isQuery** propriété a la valeur true, il ne peut pas modifier l’état de l’instance.  
  
 Pour ajouter un attribut ou une opération à un type, ouvrez le menu contextuel pour le type, choisissez **ajouter**, puis choisissez **attribut** ou **opération**.  
  
 Pour afficher ses propriétés, ouvrez le menu contextuel pour l’attribut ou l’opération, puis choisissez **propriétés**. Les propriétés s’affichent dans le **propriétés** fenêtre.  
  
 Pour afficher les propriétés de paramètres d’une opération, choisissez <strong>[...]</strong> dans le **paramètres** propriété. Une nouvelle boîte de dialogue de propriétés apparaît alors.  
  
 Pour obtenir des informations détaillées concernant l'ensemble des propriétés qu'il est possible de définir, consultez :  
  
-   [Propriétés d’attributs dans des diagrammes de classes UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
-   [Propriétés d’opérations dans des diagrammes de classes UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
### <a name="types-of-attributes-and-operations"></a>Types d'attributs et d'opérations  
 Chaque *Type* d’un attribut ou opération et chaque type de paramètre, peut prendre l’une des opérations suivantes :  
  
- **(aucun)**  -Vous pouvez laisser un type non spécifié dans la signature en omettant les deux-points précédents (`:`).  
  
- Un des types primitifs standards : **booléenne**, **entier**, **chaîne**.  
  
- Type défini dans votre modèle.  
  
- Valeur paramétrable d’un type de modèle, écrit modèle\<paramètre >. Consultez [les Types de modèle](#Templates).  
  
  Vous pouvez également écrire le nom d'un type que vous n'avez pas encore défini dans votre modèle. Le nom figurera sous **Types non spécifiés** dans l’Explorateur de modèles UML.  
  
> [!NOTE]
>  Si vous définissez ensuite une classe ou une interface de ce nom dans votre modèle, les attributs et les opérations antérieurs feront encore référence à l'élément dans Types non spécifiés. Si vous souhaitez les modifier pour faire référence à la nouvelle classe, vous devez traiter chaque attribut ou opération et réinitialiser le type, en sélectionnant la nouvelle classe dans le menu déroulant.  
  
#### <a name="multiple-types"></a>Types multiples  
 Vous pouvez définir une multiplicité de type d'attribut, d'opération ou encore de paramètre.  
  
 Les valeurs autorisées sont les suivantes :  
  
 `[1]`  
  
 Valeur du type donné. Il s'agit de la valeur par défaut.  
  
 `[0..1]`  
  
 **Null** ou une valeur du type donné.  
  
 `[*]`  
  
 Collection des nombres d’instances du type donné.  
  
 `[1..*]`  
  
 Collection d'au moins une instance du type donné.  
  
 `[n..m]`  
  
 Collection entre `n` et `m` instances du type donné.  
  
 Si la multiplicité est supérieure à 1, vous pouvez également définir les propriétés suivantes :  
  
-   **IsOrdered** : si la valeur est true, la collection présente un ordre défini.  
  
-   **IsUnique** : si la valeur est true, il n’existe aucune valeur en double dans la collection.  
  
### <a name="visibility"></a>Visibilité  
 *Visibilité* indique si l’attribut ou l’opération est accessible en dehors de la définition de classe. Les valeurs autorisées sont les suivantes :  
  
 **Public**  
  
 **+**  
  
 Accessible à partir de tous les autres types.  
  
 **Private**  
  
 **-**  
  
 Accessible uniquement par la définition interne de ce type.  
  
 **Package**  
  
 **~**  
  
 Accessible uniquement dans le package qui contient ce type, ainsi que dans tous les packages qui l'importent explicitement. Consultez [définition d’espaces de noms et les Packages](#Packages).  
  
 **Protected**  
  
 **#**  
  
 Accessible uniquement par ce type et par ceux qui héritent de lui. Consultez [héritage](#Inheritance).  
  
### <a name="setting-the-signature-of-an-attribute-or-an-operation"></a>Définition de la signature d'un attribut ou d'une opération  
 La signature d'un attribut ou d'une opération est une collection de propriétés qui inclut sa visibilité, son nom, ses paramètres (pour les opérations) et son type.  
  
 Vous pouvez écrire une signature directement dans le diagramme. Cliquez sur l'attribut ou sur l'opération pour la sélectionner, puis cliquez une nouvelle fois dessus.  
  
 Écrivez la signature comme suit :  
  
```  
visibility attribute-name : Type  
```  
  
 \- ou -  
  
```  
visibility operation-name (parameter1 : Type1, ...) : Type  
```  
  
 Exemple :  
  
```  
+ AddItem (item : MenuItem, quantity : Integer) : Boolean  
```  
  
 Utilisez la forme abrégée de visibilité. La valeur par défaut est `+` (public).  
  
 Chaque type peut correspondre à des types que vous avez définis dans le modèle, à des types standard tels qu'Entier ou Chaîne ou encore au nom d'un nouveau type que vous n'avez pas encore défini.  
  
> [!NOTE]
>  Si vous écrivez un nom sans un type dans une liste de paramètres, il indique le nom du paramètre plutôt que celui de son type. Dans cet exemple, Élément de menu et Entier deviennent les noms de deux paramètres aux types non spécifiés :  
>   
>  `AddItem(MenuItem, Integer) /* parameter names, not types! */`  
  
 Pour définir la multiplicité d'un type dans une signature, écrivez la multiplicité entre crochets à la suite du nom de type. Par exemple :  
  
```  
+ AddItems (items : MenuItem [1..*])  
+ MenuContent : MenuItem [*]  
```  
  
 Si l'attribut ou l'opération est statique, son nom apparaîtra souligné dans la signature. Si cela est abstrait, le nom s'affichera alors en italique.  
  
 Toutefois, vous pouvez uniquement définir le **Is Static** et **Is Abstract** propriétés dans le **propriétés** fenêtre.  
  
#### <a name="full-signature"></a>Signature complète  
 Lorsque vous modifiez la signature d'un attribut ou d'une opération, certaines propriétés supplémentaires peuvent apparaître à la fin de la ligne et après chaque paramètre. Elles apparaissent entre accolades {…}. Vous pouvez modifier ou ajouter ces propriétés. Par exemple :  
  
```  
+ AddItems (items: MenuItem [1..*] {unique, ordered})  
+ GetItems (filter: String) : MenuItem [*] {ordered, query}  
```  
  
 Ces propriétés sont les suivantes :  
  
 `unique`  
  
 **Est Unique**  
  
 La collection ne contient aucune valeur en double. S'applique aux types dont la multiplicité est supérieure à 1.  
  
 `ordered`  
  
 **Est ordonné**  
  
 La collection est une séquence. Si la valeur false lui est affectée, il n'existe aucun premier élément défini. S'applique aux types dont la multiplicité est supérieure à 1.  
  
 `query`  
  
 **Est la requête**  
  
 L'opération ne modifie pas l'état de son instance. S'applique uniquement aux opérations.  
  
 `/`  
  
 **Est dérivée**  
  
 L'attribut est calculé à partir de valeurs d'autres attributs ou associations.  
  
 « / » apparaît avant le nom d'un attribut. Par exemple :  
  
```  
/TotalPrice: Integer  
```  
  
 En général, la signature complète apparaît uniquement dans le diagramme pendant que vous le modifiez. Une fois la modification effectuée, les propriétés supplémentaires sont masquées. Si vous souhaitez visualiser la signature complète de tout le temps, ouvrez le menu contextuel pour le type, puis choisissez **afficher la Signature complète**.  
  
##  <a name="Associations"></a> Dessin et utilisation d’Associations  
 Utilisez une association pour représenter tout genre de liaison entre deux éléments, indépendamment de la façon dont cette liaison est implémentée dans le logiciel. Par exemple, vous pouvez utiliser une association pour représenter un pointeur en langage C#, une relation dans une base de données ou encore une référence croisée entre deux parties d'un fichier XML. Elle peut représenter une association entre des objets du monde réel, tels que la Terre et le soleil. L'association n'indique pas comment le lien est représenté, mais seulement que les informations existent.  
  
### <a name="properties-of-an-association"></a>Propriétés d'une association  
 Après avoir créé une association, définissez-en les propriétés. Ouvrez le menu contextuel pour l’association, puis choisissez **propriétés**.  
  
 Outre les propriétés de l’association dans sa globalité, chaque *rôle*, autrement dit, chaque fin de l’association, dispose de son propre quelques propriétés. Pour les visualiser, développez le **premier rôle** et **Second rôle** propriétés.  
  
 Quelques propriétés de chaque rôle sont directement visibles dans le diagramme. Elles se présentent comme suit :  
  
- Nom du rôle. Cette propriété apparaît à la fin appropriée de l'association dans le diagramme. Vous pouvez le définir sur le diagramme ou dans le **propriétés** fenêtre.  
  
- **Multiplicité**, qui utilise par défaut **1**. Cette propriété apparaît également dans le diagramme, près de la fin appropriée de l'association.  
  
- **Agrégation**. Cette propriété apparaît sous la forme d'un diamant, au niveau de l'une des extrémités du connecteur. Vous pouvez l'utiliser pour indiquer que les instances au niveau du rôle d'agrégation possèdent ou contiennent des instances de l'autre.  
  
- **Est Navigable**. Si la valeur true lui est affectée pour un seul rôle, une flèche s'affiche dans la direction navigable. Vous pouvez l'utiliser pour indiquer la navigabilité des liens et des relations de bases de données du logiciel.  
  
  Pour obtenir des informations complètes sur ces et d’autres propriétés, consultez [propriétés des associations dans UML des diagrammes de classes](../modeling/properties-of-associations-on-uml-class-diagrams.md).  
  
### <a name="navigability"></a>Navigabilité  
 Lorsque vous dessinez une association, celle-ci comporte une flèche à l'extrémité, ce qui signifie que l'association est navigable dans cette direction. Cela est utile si votre diagramme de classes représente des classes logicielles et que les associations représentent des pointeurs ou des références. Cependant, lorsque vous utilisez un diagramme de classes pour représenter des entités et des relations ou des concepts d'entreprise, il est moins approprié pour représenter la navigabilité. Dans ce cas, il est préférable de dessiner des associations sans flèches. Vous pouvez le faire en définissant le **est Navigable** propriété sur les deux terminaisons de l’association sur True. Pour simplifier ce processus, vous pouvez télécharger l’exemple de code [modélisation de domaine UML](http://code.msdn.microsoft.com/UML-Domain-Modeling-6df6f7f4).  
  
### <a name="attributes-and-associations"></a>Attributs et associations  
 Une association est une représentation graphique de l'affichage d'un attribut. Par exemple, vous pouvez dessiner une association entre Restaurant et Menu au lieu de créer une classe Restaurant avec un attribut de type Menu.  
  
 Chaque nom d'attribut devient un nom de rôle. Il apparaît à l'extrémité opposée de l'association par rapport au type propriétaire. Examinez, par exemple, `myMenu` dans l'illustration.  
  
 En général, il est préférable de n'utiliser des attributs que pour les types que vous ne dessineriez pas dans le diagramme, comme les types primitifs.  
  
 ![Association équivalente et attributs](../modeling/media/uml-classguideattrib.png "UML_ClassGuideAttrib")  
  
##  <a name="Inheritance"></a> Héritage  
 Utilisez le **héritage** outil pour créer les relations suivantes :  
  
- Un *généralisation* relation entre un type spécialisé et un type général  
  
   \- ou -  
  
- Un *réalisation* relation entre une classe et une interface qu’il implémente.  
  
  Vous ne pouvez pas créer de boucle dans les relations d'héritage.  
  
### <a name="generalization"></a>Généralisation  
 La généralisation signifie que le type de spécialisation ou dérivé hérite d'attributs, d'opérations et d'associations du type général ou de base.  
  
 Le type général apparaît à l'extrémité de la flèche de la relation.  
  
 Les opérations et attributs hérités ne sont généralement pas affichés dans les types de spécialisation. Cependant, vous pouvez ajouter des opérations héritées à la liste des opérations du type de spécialisation. Cela est particulièrement utile si vous souhaitez substituer certaines des propriétés d'une opération dans le type de spécialisation, ou encore si vous souhaitez indiquer que le code d'implémentation doit s'en charger.  
  
##### <a name="to-override-an-operations-definition-in-a-specializing-type"></a>Pour substituer une définition d'opération dans un type de spécialisation  
  
1. Cliquez sur la relation de généralisation.  
  
    Elle apparaît en surbrillance et une étiquette d’action apparaît près d’elle.  
  
2. Cliquez sur la balise d’Action, puis cliquez sur **remplacer les opérations**.  
  
    Le **remplacer les opérations** boîte de dialogue s’affiche.  
  
3. Sélectionnez les opérations que vous souhaitez apparaissent dans le type de spécialisation, puis cliquez sur **OK**.  
  
   Les opérations que vous avez sélectionnées apparaissent à présent dans le type de spécialisation.  
  
### <a name="realization"></a>Réalisation  
 La réalisation signifie qu'une classe implémente les attributs et opérations spécifiés par l'interface. L'interface se situe au niveau de l'embout de flèche du connecteur.  
  
 Lorsque vous créez un connecteur de réalisation, les opérations de l'interface sont automatiquement répliquées dans la classe de réalisation. Si vous ajoutez de nouvelles opérations à une interface, elles sont alors répliquées dans ses classes de réalisation.  
  
 Après avoir créé une relation de réalisation, vous pouvez la convertir en notation de symbole d'interface. Avec le bouton droit de la relation et choisissez **afficher sous forme d’interface (lollipop)**.  
  
 Cela vous permet d'afficher les interfaces qu'une classe implémente, sans encombrer les diagrammes de classes avec des liens de réalisation. Vous pouvez également afficher l'interface et les classes de réalisation dans des diagrammes séparés.  
  
 ![Réalisation présentée avec connecteur et lollipop](../modeling/media/uml-classguiderealize.png "UML_ClassGuideRealize")  
  
##  <a name="Templates"></a> Types de modèles  
 Vous pouvez définir un type générique ou de modèle qui peut être paramétrable par d'autres types ou valeurs.  
  
 Par exemple, vous pouvez créer un dictionnaire générique paramétrable par des types de clés et de valeurs :  
  
 ![Classe de modèle avec deux paramètres](../modeling/media/uml-classguidetemplate1.png "UML_ClassGuideTemplate1")  
  
#### <a name="to-create-a-template-type"></a>Pour créer un type de modèle  
  
1. Créez une classe ou une interface. Celle-ci figurera alors comme votre type de modèle. Nommez-la en conséquence. Par exemple, `Dictionary`.  
  
2. Ouvrez le menu contextuel pour le nouveau type, puis choisissez **propriétés**.  
  
3. Dans le **propriétés** fenêtre, cliquez sur **[...]**  dans le **paramètres de modèle** champ.  
  
    Le **éditeur de Collection de paramètres de modèle** boîte de dialogue s’affiche.  
  
4. Sélectionnez **Ajouter**.  
  
5. Affectez un nom de paramètre à la propriété de nom pour votre type de modèle (par exemple, `Key`).  
  
6. Définissez **genre de paramètre**. La valeur par défaut est **classe**.  
  
7. Si vous souhaitez que le paramètre accepte uniquement des classes dérivées d’une classe de base, définissez **valeur contrainte** à la classe de base que vous souhaitez.  
  
8. Ajoutez autant de paramètres que vous avez besoin, puis choisissez **OK**.  
  
9. Ajoutez des attributs et des opérations au type de modèle, comme vous le feriez pour d'autres classes.  
  
     Vous pouvez utiliser les paramètres dont le genre est **classe**, **Interface** ou **énumération** dans la définition d’attributs et opérations. Par exemple, vous pouvez définir cette opération dans `Key` en utilisant des classes de paramètres `Value` et `Dictionary` :  
  
     `Get(k : Key) : Value`  
  
     Vous pouvez utiliser un paramètre dont le genre est **entier** comme une limite dans une multiplicité. Par exemple, une valeur maximale de paramètre de nombre entier peut être utilisée pour définir la multiplicité d'un attribut sous la forme `[0..max]`.  
  
   Après avoir créé des types de modèles, vous pouvez les utiliser pour définir des liaisons de modèles :  
  
   ![Une classe liée à partir du modèle Dictionary](../modeling/media/uml-classguidetemplate2.png "UML_ClassGuideTemplate2")  
  
#### <a name="to-use-a-template-type"></a>Pour utiliser un type de modèle  
  
1.  Créez un type (par exemple, `AddressTable`).  
  
2.  Ouvrez le menu contextuel pour le nouveau type, puis choisissez **propriétés**.  
  
3.  Dans le **liaison de modèle** propriété, sélectionnez le type de modèle, par exemple `Dictionary`, dans la liste déroulante.  
  
4.  Développez le **liaison de modèle** propriété.  
  
     Une ligne apparaît pour chaque paramètre du type de modèle.  
  
5.  Affectez une valeur appropriée à chaque paramètre. Par exemple, affectez au paramètre `Key` une classe appelée `Name`.  
  
##  <a name="Packages"></a> Packages  
 Vous pouvez visualiser des packages dans un diagramme de classes UML. Un package est un conteneur pour d'autres éléments de modèles. Vous pouvez créer tout élément à l'intérieur d'un package. Dans le diagramme, les éléments se trouvant à l'intérieur du package se déplaceront en même temps que ce dernier.  
  
 Vous pouvez utiliser la commande de réduction/développement pour masquer ou afficher le contenu du package.  
  
 Consultez [définir des packages et des espaces de noms](../modeling/define-packages-and-namespaces.md).  
  
##  <a name="generating"></a> Génération de Code à partir de diagrammes de classes UML  
 Pour démarrer l'implémentation des classes sur un diagramme de classes UML, il est possible de générer le code C# ou de personnaliser les modèles de génération du code. Pour démarrer la génération de code à l'aide des modèles C# fournis :  
  
-   Ouvrez le menu contextuel du diagramme ou un élément, choisissez **générer le Code**, puis définissez les propriétés nécessaires.  
  
     Pour plus d’informations sur la façon de définir ces propriétés et personnalisation des modèles fournis, consultez [générer du code à partir de diagrammes de classes UML](../modeling/generate-code-from-uml-class-diagrams.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier des modèles UML et des diagrammes](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagrammes de classes UML : référence](../modeling/uml-class-diagrams-reference.md)   
 [Modéliser les besoins des utilisateurs](../modeling/model-user-requirements.md)   
 [Diagrammes de composants UML : référence](../modeling/uml-component-diagrams-reference.md)   
 [Diagrammes de séquence UML : référence](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagrammes de cas d’usage UML : référence](../modeling/uml-use-case-diagrams-reference.md)   
 [Informations de référence sur les diagrammes de composants UML](../modeling/uml-component-diagrams-reference.md)



