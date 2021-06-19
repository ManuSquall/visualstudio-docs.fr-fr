---
title: Instructions relatives à l'écriture de modèles de texte T4
description: Découvrez les recommandations générales qui sont utiles si vous générez du code de programme ou d’autres ressources d’application dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4f043e95ef477558028e634bf6b48aded2960ec2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386655"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Instructions relatives à l'écriture de modèles de texte T4

Ces recommandations générales peuvent être utiles si vous générez du code de programme ou d’autres ressources d’application dans Visual Studio. Ce ne sont pas des règles fixes.

## <a name="guidelines-for-design-time-t4-templates"></a>Instructions pour Design-Time les modèles T4

Les modèles T4 au moment du design sont des modèles qui génèrent du code dans votre projet Visual Studio au moment du Design. Pour plus d’informations, consultez [génération de code au moment du design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Générez des aspects variables de l’application.

La génération de code est particulièrement utile pour les aspects de l’application qui peuvent changer au cours du projet, ou qui seront modifiés entre les différentes versions de l’application. Séparez ces aspects variables des aspects plus invariants afin de pouvoir déterminer plus facilement ce qui doit être généré. Par exemple, si votre application fournit un site Web, séparez les fonctions de service de page standard de la logique qui définit les chemins de navigation d’une page à l’autre.

Encodez les aspects variables dans un ou plusieurs modèles sources.

Un modèle est un fichier ou une base de données que chaque modèle lit pour obtenir des valeurs spécifiques pour les parties variables du code qui doit être généré. Les modèles peuvent être des bases de données, des fichiers XML de votre propre conception, des diagrammes ou des langages spécifiques à un domaine. En règle générale, un modèle est utilisé pour générer de nombreux fichiers dans un projet Visual Studio. Chaque fichier est généré à partir d’un modèle distinct.

Vous pouvez utiliser plusieurs modèles dans un projet. Par exemple, vous pouvez définir un modèle pour la navigation entre les pages Web et un modèle distinct pour la disposition des pages.

Concentrez le modèle sur les besoins et le vocabulaire des utilisateurs, et non sur votre implémentation.

Par exemple, dans une application de site Web, vous vous attendez à ce que le modèle fasse référence à des pages Web et des liens hypertexte.

Dans l’idéal, choisissez une forme de présentation qui correspond au type d’informations que le modèle représente. Par exemple, un modèle de chemins de navigation via un site Web peut être un diagramme de cases et de flèches.

Testez le code généré.

Utilisez des tests manuels ou automatisés pour vérifier que le code qui en résulte fonctionne comme le requièrent les utilisateurs. Évitez de générer des tests à partir du même modèle que celui à partir duquel le code est généré.

Dans certains cas, les tests généraux peuvent être effectués directement sur le modèle. Par exemple, vous pouvez écrire un test qui garantit que chaque page du site Web peut être atteinte par la navigation à partir de n’importe quel autre.

Autoriser pour le code personnalisé : générer des classes partielles.

Autorisez le code que vous écrivez manuellement en plus du code généré. Il est rare qu’un schéma de génération de code soit en mesure de prendre en compte toutes les variations possibles qui peuvent se produire. Par conséquent, vous devez vous attendre à ajouter ou remplacer une partie du code généré. Lorsque la documentation générée est dans un langage .NET tel que C# ou Visual Basic, deux stratégies sont particulièrement utiles :

- Les classes générées doivent être partielles. Cela vous permet d’ajouter du contenu au code généré.

- Les classes doivent être générées par paires, l’une héritant de l’autre. La classe de base doit contenir toutes les méthodes et propriétés générées, et la classe dérivée doit contenir uniquement les constructeurs. Cela permet à votre code écrit manuellement de remplacer n’importe quelle méthode générée.

Dans d’autres langages générés tels que XML, utilisez la `<#@include#>` directive pour créer des combinaisons simples de contenu écrit et généré manuellement. Dans les cas plus complexes, vous devrez peut-être écrire une étape de validation qui associe le fichier généré à tous les fichiers écrits manuellement.

Déplacer les éléments communs dans des fichiers include ou des modèles au moment de l’exécution.

Pour éviter de répéter des blocs de texte et du code similaires dans plusieurs modèles, utilisez la `<#@ include #>` directive. Pour plus d’informations, consultez [directive include T4](../modeling/t4-include-directive.md).

Vous pouvez également générer des modèles de texte au moment de l’exécution dans un projet distinct, puis les appeler à partir du modèle au moment du Design. Pour ce faire, utilisez la `<#@ assembly #>` directive pour accéder au projet distinct.

Envisagez de déplacer de grands blocs de code dans un assembly distinct.

Si vous avez des blocs de code et des blocs de fonctionnalité de classe volumineux, il peut être utile de déplacer une partie de ce code dans les méthodes que vous compilez dans un projet distinct. Vous pouvez utiliser la `<#@ assembly #>` directive pour accéder au code dans le modèle. Pour plus d’informations, consultez [directive d’assembly T4](../modeling/t4-assembly-directive.md).

Vous pouvez placer les méthodes dans une classe abstraite que le modèle peut hériter. La classe abstraite doit hériter de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> . Pour plus d’informations, consultez [directive de modèle T4](../modeling/t4-template-directive.md).

Générez du code, et non des fichiers de configuration.

L’une des méthodes d’écriture d’une application variable consiste à écrire un code de programme générique qui accepte un fichier de configuration. Une application écrite de cette manière est très flexible et peut être reconfigurée lorsque les besoins de l’entreprise évoluent, sans régénérer l’application. Toutefois, l’inconvénient de cette approche est que l’application s’exécute moins bien qu’une application plus spécifique. En outre, son code de programme sera plus difficile à lire et à gérer, en partie parce qu’il a toujours à gérer les types génériques.

En revanche, une application dont les parties variables sont générées avant la compilation peut être fortement typée. Il est ainsi beaucoup plus facile et plus fiable d’écrire du code écrit manuellement et de l’intégrer aux parties générées du logiciel.

Pour tirer pleinement parti de la génération de code, essayez de générer du code de programme au lieu de fichiers de configuration.

Utilisez un dossier de code généré.

Placez les modèles et les fichiers générés dans un dossier de projet nommé **code généré**, pour préciser que ces fichiers ne sont pas des fichiers qui doivent être modifiés directement. Si vous créez un code personnalisé pour remplacer ou ajouter des classes générées, placez-les dans un dossier nommé **code personnalisé**. La structure d’un projet standard ressemble à ceci :

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

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Instructions pour les modèles T4 Run-Time (prétraités)

Déplacez le matériel commun dans les modèles hérités.

Vous pouvez utiliser l’héritage pour partager des méthodes et des blocs de texte entre les modèles de texte T4. Pour plus d’informations, consultez [directive de modèle T4](../modeling/t4-template-directive.md).

Vous pouvez également utiliser des fichiers include dotés de modèles au moment de l’exécution.

Déplacez de grands corps de code dans une classe partielle.

Chaque modèle au moment de l’exécution génère une définition de classe partielle qui porte le même nom que le modèle. Vous pouvez écrire un fichier de code qui contient une autre définition partielle de la même classe. Vous pouvez ajouter des méthodes, des champs et des constructeurs à la classe de cette manière. Ces membres peuvent être appelés à partir des blocs de code dans le modèle.

L’avantage de cette opération est que le code est plus facile à écrire, car IntelliSense est disponible. En outre, vous pouvez obtenir une meilleure séparation entre la présentation et la logique sous-jacente.

Par exemple, dans **MyReportText.TT**:

`The total is: <#= ComputeTotal() #>`

Dans **MyReportText-methods. cs**:

`private string ComputeTotal() { ... }`

Autoriser pour le code personnalisé : fournissez des points d’extension.

Envisagez de générer des méthodes virtuelles dans \<#+ class feature blocks #> . Cela permet d’utiliser un modèle unique dans de nombreux contextes sans modification. Au lieu de modifier le modèle, vous pouvez construire une classe dérivée qui fournit la logique supplémentaire minimale. La classe dérivée peut être du code normal ou peut être un modèle d’exécution.

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

Collecte de données distincte à partir de la génération de texte.

Essayez d’éviter de mélanger des blocs de calcul et de texte. Dans chaque modèle de texte, utilisez le premier \<# code block #> pour définir des variables et effectuer des calculs complexes. Du premier bloc de texte jusqu’à la fin du modèle ou du premier \<#+ class feature block #> , évitez les expressions longues et évitez les boucles et les conditions, sauf si elles contiennent des blocs de texte. Cette pratique rend le modèle plus facile à lire et à gérer.

N’utilisez pas `.tt` pour les fichiers include.

Utilisez une extension de nom de fichier différente comme `.ttinclude` pour les fichiers include. Utilisez `.tt` uniquement pour les fichiers que vous souhaitez traiter en tant que modèles de texte au moment de l’exécution ou au moment du Design. Dans certains cas, Visual Studio reconnaît les `.tt` fichiers et définit automatiquement leurs propriétés pour le traitement.

Démarrez chaque modèle en tant que prototype fixe.

Écrivez un exemple de code ou de texte que vous souhaitez générer, et assurez-vous qu’il est correct. Ensuite, remplacez son extension par. TT et insérez de manière incrémentielle le code qui modifie le contenu en lisant le modèle.

Envisagez d’utiliser des modèles typés.

Bien que vous puissiez créer un schéma XML ou de base de données pour vos modèles, il peut être utile de créer un langage spécifique à un domaine (DSL). Un DSL présente l’avantage de générer une classe pour représenter chaque nœud dans le schéma et des propriétés pour représenter les attributs. Cela signifie que vous pouvez programmer en termes de modèle d’entreprise. Exemple :

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

Envisagez d’utiliser des diagrammes pour vos modèles.

De nombreux modèles sont présentés le plus efficacement et gérés simplement comme des tables de texte, en particulier si elles sont très volumineuses.

Toutefois, pour certains types d’exigences d’entreprise, il est important de clarifier des ensembles complexes de relations et de flux de travail, et les diagrammes sont le moyen le plus adapté. L’un des avantages d’un diagramme est qu’il est facile à aborder avec les utilisateurs et les autres parties prenantes. En générant du code à partir d’un modèle au niveau des besoins de l’entreprise, vous rendez votre code plus flexible lorsque les exigences changent.

Vous pouvez également concevoir votre propre type de diagramme comme un langage spécifique à un domaine (DSL). Le code peut être généré à partir des langages UML et DSL. Pour plus d’informations, consultez [analyse et modélisation](../modeling/analyze-and-model-your-architecture.md)de l’architecture.

## <a name="see-also"></a>Voir aussi

- [Génération de code durant la conception à l'aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Génération de texte durant l'exécution à l'aide des modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
