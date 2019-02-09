---
title: Instructions relatives à l'écriture de modèles de texte T4
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 410ab74e672d29673674131b30e2412581b9b399
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954203"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Instructions relatives à l'écriture de modèles de texte T4
Ces instructions générales peuvent être utiles si vous générez du code de programme ou d’autres ressources de l’application dans Visual Studio. Ils ne sont pas fixes règles.

## <a name="guidelines-for-design-time-t4-templates"></a>Instructions pour les modèles T4 au moment du Design
 Les modèles T4 au moment du design sont des modèles qui génèrent du code dans votre projet Visual Studio au moment du design. Pour plus d’informations, consultez [génération de Code au moment du Design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

 Générer des aspects variables de l’application.
Génération de code est particulièrement utile pour les aspects de l’application qui peut être modifiée au cours du projet, ou modifié entre les différentes versions de l’application. Séparer ces aspects variables plus constants, afin que vous pouvez déterminer plus facilement ce qui doit être généré. Par exemple, si votre application fournit un site Web, séparez la page standard desservant des fonctions à partir de la logique qui définit les chemins d’accès de navigation d’une page à un autre.

 Encodez les aspects variables dans un ou plusieurs modèles de code source.
Un modèle est un fichier ou une base de données que chaque modèle lit pour obtenir des valeurs spécifiques pour les parties variables du code qui doit être généré. Modèles peuvent être des bases de données, les fichiers XML de votre propre conception, les diagrammes ou les langages spécifiques à un domaine. En règle générale, un seul modèle est utilisé pour générer de nombreux fichiers dans un projet Visual Studio. Chaque fichier est généré à partir d’un modèle séparé.

 Vous pouvez utiliser plusieurs modèles dans un projet. Par exemple, vous pouvez définir un modèle pour la navigation entre pages web et un modèle distinct de la disposition des pages.

 Le modèle de nous concentrer sur le vocabulaire et les besoins des utilisateurs, et non sur votre implémentation.
Par exemple, dans une application de site Web, vous vous attendez le modèle pour faire référence à des pages web et des liens hypertexte.

 Dans l’idéal, choisir un formulaire de présentation qui convient le type d’information qui représente le modèle. Par exemple, un modèle de chemins d’accès de navigation d’un site Web peut être un diagramme des zones et des flèches.

 Tester le code généré.
Utiliser des tests manuels ou automatisés pour vérifier que le code résultant fonctionne comme les utilisateurs ont besoin. Éviter de générer des tests à partir du même modèle à partir duquel le code est généré.

 Dans certains cas, les tests générales peuvent être effectuées directement sur le modèle. Par exemple, vous pouvez écrire un test qui garantit que chaque page dans le site Web peut être atteint par la navigation à partir d’autres.

 Autoriser un code personnalisé : générer des classes partielles.
Autoriser pour le code que vous écrivez à la main en outre le code généré. Il est rare qu’un schéma de génération de code pour être en mesure de prendre en compte toutes les variations possibles qui peuvent se produire. Par conséquent, vous devriez ajouter ou remplacer une partie du code généré. Où les données générées sont dans un langage .NET comme [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], deux stratégies sont particulièrement utiles :

- Les classes générées doivent être partielles. Vous pouvez ainsi ajouter du contenu au code généré.

- Classes doivent être générées par paires, une héritant de l’autre. La classe de base doit contenir toutes les propriétés et méthodes générées, et la classe dérivée doit contenir uniquement les constructeurs. Cela permet à votre code écrit manuellement remplacer les méthodes générées.

  Dans d’autres langages générés tels que XML, utilisez la `<#@include#>` directive pour créer des combinaisons simples du contenu généré et écrit manuellement. Dans les cas plus complexes, vous devrez peut-être écrire une étape de post-traitement qui combine le fichier généré avec les fichiers écrits manuellement.

  Déplacer le matériel commun dans les fichiers include ou les modèles au moment de l’exécution.
  Pour éviter de répéter des blocs identiques de texte et de code dans plusieurs modèles, utilisez la `<#@ include #>` directive. Pour plus d’informations, consultez [Directive Include de T4](../modeling/t4-include-directive.md).

  Vous pouvez également créer des modèles de texte de l’exécution dans un projet distinct et les appeler à partir du modèle au moment du design. Pour ce faire, utilisez la `<#@ assembly #>` directive pour accéder au projet distinct. Pour obtenir des exemples, consultez [« L’héritage dans modèles de texte » dans le Blog de Gareth Jones](http://go.microsoft.com/fwlink/?LinkId=208373).

  Envisagez de déplacer de grands blocs de code dans un assembly distinct.
  Si vous avez des grands blocs de code et des blocs de fonctionnalité de classe, il peut être utile de déplacer une partie de ce code en méthodes que vous compilez dans un projet distinct. Vous pouvez utiliser la `<#@ assembly #>` directive pour accéder au code dans le modèle. Pour plus d’informations, consultez [Directive d’Assembly T4](../modeling/t4-assembly-directive.md).

  Vous pouvez placer les méthodes dans une classe abstraite qui peut hériter de celui-ci. La classe abstraite doit hériter <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Pour plus d’informations, consultez [Directive du modèle T4](../modeling/t4-template-directive.md).

  Générer du code, pas les fichiers de configuration.
  Une méthode d’écriture d’une application variable consiste à écrire du code de programme générique qui accepte un fichier de configuration. Une application écrite de cette manière est très flexible et peut être reconfigurée lorsque les besoins changent, sans recréer l’application. Toutefois, l’inconvénient de cette approche est que l’application sera moins performante qu’une application plus spécifique. En outre, son code de programme sera plus difficile à lire et à gérer, en partie parce qu’il doit toujours prendre en compte avec les types les plus génériques.

  En revanche, une application dont les parties variables sont générées avant la compilation peut être fortement typée. Cela rend beaucoup plus faciles et plus fiables pour écrire du code écrit manuellement et l’intégrer avec les parties du logiciel.

  Pour obtenir le meilleur parti de la génération de code, essayez de générer du code de programme au lieu de fichiers de configuration.

  Utiliser un dossier Code généré.
  Placez les modèles et les fichiers générés dans un dossier de projet nommé **le Code généré**, afin de pouvoir effacer que ceux-ci ne sont pas des fichiers qui doivent être modifiées directement. Si vous créez un code personnalisé pour remplacer ou compléter les classes générées, placez ces classes dans un dossier nommé **Code personnalisé**. La structure d’un projet classique ressemble à ceci :

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

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Instructions pour les modèles T4 (prétraité) d’exécution
 Déplacer le matériel commun vers des modèles hérités.
Vous pouvez utiliser l’héritage pour partager des méthodes et des blocs de texte entre les modèles de texte T4. Pour plus d’informations, consultez [Directive du modèle T4](../modeling/t4-template-directive.md).

 Vous pouvez également utiliser incluent des fichiers qui ont des modèles au moment de l’exécution.

 Déplacer des corps de code volumineux dans une classe partielle.
Chaque modèle au moment de l’exécution génère une définition de classe partielle qui a le même nom que le modèle. Vous pouvez écrire un fichier de code qui contient une autre définition partielle de la même classe. Vous pouvez ajouter des méthodes, des champs et des constructeurs pour la classe de cette manière. Ces membres peuvent être appelés depuis les blocs de code dans le modèle.

 Un avantage de cette procédure est que le code est plus facile à écrire, car IntelliSense est disponible. En outre, vous pouvez obtenir une meilleure séparation entre la présentation et la logique sous-jacente.

 Par exemple, dans **MyReportText.tt**:

 `The total is: <#= ComputeTotal() #>`

 Dans **MyReportText-Methods.cs**:

 `private string ComputeTotal() { ... }`

 Autoriser un code personnalisé : fournir des points d’extension.
Envisagez de générer des méthodes virtuelles dans \<fonctionnalité de classe #+ bloque #>. Ainsi, un modèle unique être utilisé dans de nombreux contextes sans modification. Au lieu de modifier le modèle, vous pouvez construire une classe dérivée qui fournit la logique supplémentaire minimale. La classe dérivée peut être du code normal, ou il peut être un modèle au moment de l’exécution.

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

## <a name="guidelines-for-all-t4-templates"></a>Instructions pour tous les modèles T4
 Séparer la collecte de données à partir de la génération de texte.
Essayez d’éviter de mélanger les calculs et les blocs de texte. Dans chaque modèle de texte, utilisez la première \<# de bloc de code de # > pour définir des variables et effectuer des calculs complexes. À partir du premier bloc de texte jusqu'à la fin du modèle ou la première \<fonctionnalité de classe #+ bloquer #>, éviter les expressions longues et éviter les boucles et des instructions conditionnelles, sauf si elles contiennent des blocs de texte. Cette pratique rend le modèle plus facile à lire et à gérer.

 N’utilisez pas `.tt` pour les fichiers include.
Utiliser une extension de nom de fichier différent tel que `.ttinclude` pour les fichiers include. Utilisez `.tt` uniquement pour les fichiers que vous souhaitez être traités comme exécution soit au moment du design des modèles de texte. Dans certains cas, Visual Studio reconnaît `.tt` fichiers et définit automatiquement leurs propriétés pour le traitement.

 Commencez chaque modèle comme un prototype fixe.
Écrire un exemple de code ou du texte que vous souhaitez générer et assurez-vous qu’il est correct. Puis remplacez son extension .tt et insérez le code qui modifie le contenu en lisant le modèle de façon incrémentielle.

 Envisagez d’utiliser des modèles typés.
Bien que vous pouvez créer un schéma XML ou de base de données pour vos modèles, il peut être utile de créer un langage spécifique du domaine (DSL). Une solution DSL présente l’avantage qu’elle génère une classe pour représenter chaque nœud dans le schéma et les propriétés pour représenter les attributs. Cela signifie que vous pouvez programmer le modèle d’entreprise. Exemple :

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

 Envisagez d’utiliser des diagrammes pour vos modèles.
De nombreux modèles de présenter plus efficacement et gérés simplement comme des tables de texte, en particulier si elles sont très volumineuses.

 Toutefois, pour certains types de besoins de l’entreprise, il est important de clarifier les jeux complexes de relations et de flux de travail et les diagrammes sont le support le mieux adapté. Un avantage d’un diagramme est qu’il est facile de discuter avec les utilisateurs et les autres parties prenantes. En générant le code à partir d’un modèle au niveau des besoins de l’entreprise, vous rendez votre code plus flexible lorsque les besoins changent.

 Vous pouvez également concevoir votre propre type de diagramme comme un langage spécifique à un domaine (DSL). Code peut être généré à partir de UML et DSL. Pour plus d’informations, consultez [analyse et la modélisation de l’Architecture](../modeling/analyze-and-model-your-architecture.md).

## <a name="see-also"></a>Voir aussi

- [Génération de code au moment du design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Génération de texte à l’exécution à l’aide des modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
