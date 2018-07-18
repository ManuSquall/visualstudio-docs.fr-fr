---
title: Instructions relatives à l'écriture de modèles de texte T4
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f96cea682699382b55b786001a175616c877804a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31953614"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Instructions relatives à l'écriture de modèles de texte T4
Ces instructions générales peuvent être utiles si vous générez du code de programme ou d’autres ressources de l’application dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Ils ne sont pas fixes règles.

## <a name="guidelines-for-design-time-t4-templates"></a>Recommandations pour les modèles T4 au moment du Design
 Les modèles T4 au moment du design sont des modèles qui génèrent du code dans votre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet au moment du design. Pour plus d’informations, consultez [génération du Code à l’aide de modèles de texte T4 au moment du Design](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

 Générer des aspects variables de l’application.
Génération de code est plus utile pour les aspects de l’application qui peut être modifiée au cours du projet, ou changeront entre différentes versions de l’application. Séparer ces aspects variables plus constants, afin que vous pouvez déterminer plus facilement ce qui doit être généré. Par exemple, si votre application fournit un site Web, séparez la page standard servant des fonctions à partir de la logique qui définit les chemins d’accès de navigation d’une page à l’autre.

 Encodez les aspects variables dans un ou plusieurs modèles de code source.
Un modèle est un fichier ou la base de données de chaque modèle lit pour obtenir des valeurs spécifiques pour les parties variables du code qui doit être créé. Modèles peuvent être des bases de données, les fichiers XML de votre propre conception, les diagrammes ou les langages spécifiques à un domaine. En règle générale, un modèle est utilisé pour générer de nombreux fichiers dans un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet. Chaque fichier est généré à partir d’un modèle séparé.

 Vous pouvez utiliser plusieurs modèles dans un projet. Par exemple, vous pouvez définir un modèle pour la navigation entre pages Web et un modèle distinct de la disposition des pages.

 Le modèle vous concentrer sur le vocabulaire et les besoins des utilisateurs, et non sur votre implémentation.
Par exemple, dans une application de site Web, vous vous attendez le modèle pour faire référence à des pages Web et des liens hypertexte.

 Dans l’idéal, choisissez une forme de présentation adaptée au genre d’informations sur le modèle. Par exemple, un modèle de chemins de navigation dans un site Web peut être un diagramme des zones et des flèches.

 Tester le code généré.
Utilisez les tests manuels ou automatisés pour vérifier que le code résultant fonctionne comme les utilisateurs ont besoin. Éviter de générer des tests à partir du même modèle à partir duquel le code est généré.

 Dans certains cas, les tests générales peuvent être exécutés directement sur le modèle. Par exemple, vous pouvez écrire un test qui garantit que chaque page dans le site Web peut être atteint par la navigation à partir de n’importe quel autre.

 Autoriser le code personnalisé : générer des classes partielles.
Autoriser pour le code que vous écrivez manuellement en plus du code généré. Il est rare qu’un schéma de génération de code pouvoir prendre en compte toutes les variations possibles qui peuvent se produire. Par conséquent, vous devriez compléter ou remplacer une partie du code généré. Où les données générées sont dans un langage .NET tel que [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], deux stratégies sont particulièrement utiles :

-   Les classes générées doivent être partielles. Vous pouvez ainsi ajouter du contenu au code généré.

-   Classes doivent être générées par paires, une héritant de l’autre. La classe de base doit contenir toutes les propriétés et méthodes générées, et la classe dérivée doit contenir uniquement les constructeurs. Cela permet à votre code écrit manuellement remplacer une des méthodes générées.

 Dans d’autres langages générés tels que XML, utilisez la `<#@include#>` directive pour créer des combinaisons simples de contenus généré et écrit manuellement. Dans des cas plus complexes, vous devrez peut-être écrire une étape de post-traitement qui combine le fichier généré avec les fichiers écrits manuellement.

 Déplacer le matériel commun dans des fichiers include ou de modèles au moment de l’exécution pour éviter de répéter comme blocs de texte et de code dans plusieurs modèles, utilisent le `<#@ include #>` la directive. Pour plus d’informations, consultez [Directive Include de T4](../modeling/t4-include-directive.md).

 Vous pouvez également générer des modèles de texte au moment de l’exécution dans un projet distinct et puis de les appeler à partir du modèle au moment du design. Pour ce faire, utilisez la `<#@ assembly #>` directive pour accéder au projet séparé. Pour obtenir des exemples, consultez [« D’héritage de modèles de texte » dans le Blog de Gareth Jones](http://go.microsoft.com/fwlink/?LinkId=208373).

 Envisagez de déplacer de grands blocs de code dans un assembly distinct.
 Si vous possédez de grands blocs de code et des blocs de fonctionnalité de classe, il peut être utile de déplacer une partie de ce code dans des méthodes que vous compilez dans un projet distinct. Vous pouvez utiliser la `<#@ assembly #>` directive pour accéder au code dans le modèle. Pour plus d’informations, consultez [Directive d’Assembly T4](../modeling/t4-assembly-directive.md).

 Vous pouvez placer les méthodes dans une classe abstraite qui peut hériter que le modèle. La classe abstraite doit hériter de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Pour plus d’informations, consultez [Directive du modèle T4](../modeling/t4-template-directive.md).

 Générer du code, pas les fichiers une méthode de configuration de l’écriture d’une application variable consiste à écrire du code de programme générique qui accepte un fichier de configuration. Une application écrite de cette façon est très flexible et peut être reconfigurée lorsque les besoins changent, sans la reconstruction de l’application. Toutefois, l’inconvénient de cette approche est que l’application sera moins performante qu’une application plus spécifique. En outre, son code de programme sera plus difficile à lire et à gérer, en partie parce qu’il doit toujours prendre en compte avec les types plus génériques.

 En revanche, une application dont les parties variables sont générées avant la compilation peut être fortement typée. Il est ainsi beaucoup plus faciles et plus fiables pour écrire du code écrit manuellement et l’intégrer avec les parties du logiciel.

 Pour obtenir le meilleur parti de la génération de code, essayez de générer du code de programme au lieu des fichiers de configuration.

 Utilisez un dossier de Code généré placez les modèles et les fichiers générés dans un dossier de projet nommé **Code généré**, afin de pouvoir effacer que ceux-ci ne sont pas des fichiers qui doivent être modifiés directement. Si vous créez un code personnalisé pour remplacer ou ajouter des classes générées, placez ces classes dans un dossier nommé **Code personnalisé**. La structure d’un projet classique ressemble à ceci :

```
MyProject
   Custom Code
      Class1.cs
      Class2.cs
   Generated Code
      Class1.tt
          Class1.cs
      Class2.tt
          Class2.cs
   AnotherClass.cs

```

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Recommandations pour les modèles T4 de (prétraités) au moment de l’exécution
 Déplacer le matériel commun vers des modèles hérités, vous pouvez utiliser l’héritage pour partager des méthodes et des blocs de texte entre les modèles de texte T4. Pour plus d’informations, consultez [Directive du modèle T4](../modeling/t4-template-directive.md).

 Vous pouvez également utiliser des fichiers include qui ont des modèles au moment de l’exécution.

 Déplacer des corps de code volumineux dans une classe partielle.
Chaque modèle au moment de l’exécution génère une définition de classe partielle qui porte le même nom que le modèle. Vous pouvez écrire un fichier de code qui contient une autre définition partielle de la même classe. Vous pouvez ajouter des méthodes, champs et des constructeurs pour la classe de cette manière. Ces membres peuvent être appelés à partir de blocs de code dans le modèle.

 Un avantage est que le code est plus facile à écrire, car IntelliSense est disponible. En outre, vous pouvez obtenir une meilleure séparation entre la présentation et la logique sous-jacente.

 Par exemple, dans **MyReportText.tt**:

 `The total is: <#= ComputeTotal() #>`

 Dans **MyReportText-Methods.cs**:

 `private string ComputeTotal() { ... }`

 Autoriser le code personnalisé : fournir des points d’extension envisagez de générer des méthodes virtuelles dans \<# des blocs de fonctionnalité de classe #+ >. Cela permet à un seul modèle à utiliser dans de nombreux contextes sans modification. Au lieu de modifier le modèle, vous pouvez construire une classe dérivée qui fournit la logique supplémentaire minimum. La classe dérivée peut être du code normal, ou il peut être un modèle au moment de l’exécution.

 Par exemple, dans MyStandardRunTimeTemplate.tt :

```
This page is copyright <#= CompanyName() #>.
<#+ protected virtual string CompanyName() { return ""; } #>
```

 Dans le code d’une application :

```
class FabrikamTemplate : MyStandardRunTimeTemplate
{
  protected override string CompanyName() { return "Fabrikam"; }
}
...
  string PageToDisplay = new FabrikamTemplate().TextTransform();

```

## <a name="guidelines-for-all-t4-templates"></a>Recommandations pour tous les modèles T4
 Collecte de données distincte de la génération de texte essayez d’éviter de mélanger les calculs et les blocs de texte. Dans chaque modèle de texte, utilisez la première \<# de bloc de code de # > pour définir des variables et effectuer des calculs complexes. Dans le premier bloc de texte jusqu'à la fin du modèle ou la première \<fonctionnalité de classe #+ bloc #>, évitez d’expressions longues et éviter les boucles et les instructions conditionnelles, sauf si elles contiennent des blocs de texte. Cette pratique rend le modèle plus facile à lire et à gérer.

 N’utilisez pas `.tt` pour inclure les fichiers utilisent une extension de nom de fichier différent tel que `.ttinclude` pour les fichiers include. Utilisez `.tt` uniquement pour les fichiers que vous souhaitez être traités comme exécution soit au moment du design des modèles de texte. Dans certains cas, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] reconnaît `.tt` fichiers et définit automatiquement leurs propriétés pour le traitement.

 Démarrer chaque modèle comme un prototype fixe.
Écrivez un exemple de code ou du texte que vous souhaitez générer et assurez-vous qu’il est correct. Puis remplacez son extension .tt et insérez le code qui modifie le contenu en lisant le modèle de façon incrémentielle.

 Envisagez d’utiliser des modèles typés.
Bien que vous pouvez créer un schéma XML ou de base de données pour vos modèles, il peut être utile de créer un langage spécifique à un domaine (DSL). Une DSL présente l’avantage qu’il génère une classe pour représenter chaque nœud dans le schéma et des propriétés pour représenter les attributs. Cela signifie que vous pouvez programmer le modèle d’entreprise. Par exemple :

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

 Envisagez d’utiliser des diagrammes pour vos modèles.
De nombreux modèles sont plus efficacement présentées et gérés simplement comme des tables de texte, en particulier s’ils sont très volumineux.

 Toutefois, pour certains types de besoins de l’entreprise, il est important de clarifier les jeux complexes de relations et de flux de travail et les diagrammes sont le support le mieux adapté. Le des avantages d’un diagramme sont qu’il est facile de discuter avec les utilisateurs et les autres parties prenantes. En générant le code à partir d’un modèle au niveau des besoins de l’entreprise, vous rendez votre code plus flexible lorsque les spécifications changent.

 Vous pouvez également concevoir votre propre type de diagramme comme un langage spécifique à un domaine (DSL). Code peut être généré à partir d’UML et DSL. Pour plus d’informations, consultez [analyse et modélisation de l’Architecture](../modeling/analyze-and-model-your-architecture.md).

## <a name="see-also"></a>Voir aussi

- [Génération de code au moment du design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Génération de texte à l’exécution à l’aide des modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
