---
title: "Instructions pour l’écriture de modèles de texte T4 | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04dd3fc4-10e8-488a-bdea-4d615f50f063
caps.latest.revision: 9
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 7d9dd7193455a625b0410eaca3b2bd243c109743
ms.lasthandoff: 02/22/2017

---
# <a name="guidelines-for-writing-t4-text-templates"></a>Instructions relatives à l'écriture de modèles de texte T4
Ces instructions générales peuvent être utiles si vous générez du code de programme ou d’autres ressources de l’application dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Ils ne sont pas fixes règles.  
  
## <a name="guidelines-for-design-time-t4-templates"></a>Instructions pour les modèles T4 au moment du Design  
 Les modèles T4 au moment du design sont des modèles qui génèrent du code dans votre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet au moment du design. Pour plus d’informations, consultez [génération du Code à l’aide de modèles de texte T4 au moment du Design](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Générez des aspects variables de l’application.  
 Génération de code est très utile pour les aspects de l’application qui peuvent changer au cours du projet ou changeront entre différentes versions de l’application. Séparez ces aspects variables plus constants afin que vous pouvez déterminer plus facilement ce qui doit être généré. Par exemple, si votre application fournit un site Web, séparez la page standard servant de fonctions à partir de la logique qui définit les chemins de navigation d’une page à l’autre.  
  
 Encodez les aspects variables dans un ou plusieurs modèles de code source.  
 Un modèle est un fichier ou une base de données de chaque modèle lit pour obtenir des valeurs spécifiques pour les parties variables du code qui doit être générée. Modèles peuvent être des bases de données, les fichiers XML de votre propre conception, des diagrammes ou langages spécifiques au domaine. En règle générale, un modèle est utilisé pour générer de nombreux fichiers dans un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet. Chaque fichier est généré à partir d’un modèle séparé.  
  
 Vous pouvez utiliser plusieurs modèles dans un projet. Par exemple, vous pouvez définir un modèle pour la navigation entre les pages Web et un modèle séparé pour la disposition des pages.  
  
 Le modèle nous concentrer sur le vocabulaire et les besoins des utilisateurs, et non sur votre implémentation.  
 Par exemple, dans une application de site Web, vous vous attendez le modèle pour faire référence à des pages Web et des liens hypertexte.  
  
 Dans l’idéal, choisissez une forme de présentation adaptée au genre d’informations qui représente le modèle. Par exemple, un modèle de chemins de navigation via un site Web peut être un diagramme de cases et de flèches.  
  
 Tester le code généré.  
 Utiliser des tests manuels ou automatisés pour vérifier que le code résultant fonctionne comme les utilisateurs ont besoin. Éviter de générer des tests à partir du même modèle à partir duquel le code est généré.  
  
 Dans certains cas, des tests généraux peuvent effectuées directement sur le modèle. Par exemple, vous pouvez écrire un test qui garantit que chaque page du site Web peut être atteint par la navigation à partir de n’importe quel autre.  
  
 Autoriser le code personnalisé : générer des classes partielles.  
 Autoriser pour le code que vous écrivez manuellement en plus du code généré. Il est rare qu’un schéma de génération de code pouvoir prendre en compte toutes les variations possibles qui peuvent se produire. Par conséquent, vous devriez compléter ou remplacer une partie du code généré. Où les données générées sont dans un langage .NET tel que [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], deux stratégies sont particulièrement utiles :  
  
-   Les classes générées doivent être partielles. Vous pouvez ainsi ajouter du contenu au code généré.  
  
-   Classes doivent être générées par paires, une héritant de l’autre. La classe de base doit contenir toutes les propriétés et méthodes générées, et la classe dérivée doit contenir uniquement les constructeurs. Cela permet à votre code écrit manuellement remplacer une des méthodes générées.  
  
 Dans d’autres langages générés tels que XML, utilisez la `<#@include#>` directive permettant de créer des combinaisons simples de contenus généré et écrit manuellement. Dans des cas plus complexes, vous devrez peut-être écrire une étape de post-traitement qui combine le fichier généré avec les fichiers écrits manuellement.  
  
 Déplacer le matériel commun vers les fichiers include ou les modèles au moment de l’exécution  
 Pour éviter de répéter comme blocs de texte et de code dans plusieurs modèles, utilisez la `<#@ include #>` directive. Pour plus d’informations, consultez [Directive Include de T4](../modeling/t4-include-directive.md).  
  
 Vous pouvez également créer des modèles de texte au moment de l’exécution dans un projet distinct et les appeler à partir du modèle au moment du design. Pour ce faire, utilisez la `<#@ assembly #>` directive pour accéder au projet séparé. Pour obtenir des exemples, consultez [« Héritage de modèles de texte » dans le Blog de Gareth Jones](http://go.microsoft.com/fwlink/?LinkId=208373).  
  
 Envisagez de déplacer de grands blocs de code dans un assembly distinct.  
 Si vous possédez de grands blocs de code et des blocs de fonctionnalité de classe, il peut être utile de déplacer une partie de ce code dans les méthodes que vous compilez dans un projet distinct. Vous pouvez utiliser la `<#@ assembly #>` directive pour accéder au code dans le modèle. Pour plus d’informations, consultez [Directive d’Assembly T4](../modeling/t4-assembly-directive.md).  
  
 Vous pouvez placer les méthodes dans une classe abstraite qui peut hériter de modèle. La classe abstraite doit hériter de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>.</xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> Pour plus d’informations, consultez [Directive du modèle T4](../modeling/t4-template-directive.md).  
  
 Générer du code, pas les fichiers de configuration  
 Une méthode d’écriture d’une application variable consiste à écrire du code de programme générique qui accepte un fichier de configuration. Une application écrite de cette façon est très flexible et peut être reconfigurée lorsque les besoins changent, sans recréer l’application. Toutefois, l’inconvénient de cette approche est que l’application sera moins performante qu’une application plus spécifique. En outre, son code de programme sera plus difficile à lire et à gérer, en partie parce qu’il doit toujours prendre en compte avec les types les plus génériques.  
  
 En revanche, une application dont les parties variables sont générées avant la compilation peut être fortement typée. Il est beaucoup plus faciles et plus fiables d’écrire du code écrit manuellement et son intégration avec les parties du logiciel.  
  
 Pour obtenir le meilleur parti de la génération de code, essayez de générer du code de programme au lieu des fichiers de configuration.  
  
 Utiliser un dossier Code généré  
 Placez les modèles et les fichiers générés dans un dossier de projet nommé **Code généré**, afin de pouvoir effacer que ceux-ci ne sont pas des fichiers qui doivent être modifiés directement. Si vous créez un code personnalisé pour remplacer ou compléter les classes générées, placez ces classes dans un dossier nommé **Code personnalisé**. La structure d’un projet typique ressemble à ceci :  
  
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
  
## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Instructions pour les modèles T4 (prétraités) d’exécution  
 Déplacer le matériel commun vers des modèles hérités  
 Vous pouvez utiliser l’héritage pour partager des méthodes et des blocs de texte entre les modèles de texte T4. Pour plus d’informations, consultez [Directive du modèle T4](../modeling/t4-template-directive.md).  
  
 Vous pouvez également utiliser des fichiers qui ont des modèles au moment de l’exécution.  
  
 Déplacer des corps de code volumineux dans une classe partielle.  
 Chaque modèle au moment de l’exécution génère une définition de classe partielle qui porte le même nom que le modèle. Vous pouvez écrire un fichier de code qui contient une autre définition partielle de la même classe. Vous pouvez ajouter des méthodes, des champs et des constructeurs à la classe de cette manière. Ces membres peuvent être appelés à partir de blocs de code dans le modèle.  
  
 L’avantage de cette opération est que le code est plus facile à écrire, car IntelliSense est disponible. En outre, vous pouvez obtenir une meilleure séparation entre la présentation et la logique sous-jacente.  
  
 Par exemple, dans **MyReportText.tt**:  
  
 `The total is: <#= ComputeTotal() #>`  
  
 Dans **MyReportText-Methods.cs**:  
  
 `private string ComputeTotal() { ... }`  
  
 Autoriser le code personnalisé : fournir des points d’extension  
 Envisagez de générer des méthodes virtuelles dans \<# des blocs de fonctionnalité de classe #+ >. Ainsi, un modèle unique être utilisé dans de nombreux contextes sans modification. Au lieu de modifier le modèle, vous pouvez créer une classe dérivée qui fournit la logique supplémentaire minimum. La classe dérivée peut être du code normal, ou il peut être un modèle au moment de l’exécution.  
  
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
 Collecte de données séparée de la génération de texte  
 Essayez d’éviter de mélanger les calculs et les blocs de texte. Dans chaque modèle de texte, utilisez la première \<du code # bloc #> pour définir des variables et effectuer des calculs complexes. Dans le premier bloc de texte jusqu'à la fin du modèle ou la première \<fonctionnalité de classe #+ bloquer #>, évitez d’expressions longues et éviter les boucles et les instructions conditionnelles, sauf si elles contiennent des blocs de texte. Cette pratique rend le modèle le plus facile à lire et à gérer.  
  
 N’utilisez pas `.tt` pour les fichiers include  
 Utilisez une extension de nom de fichier différent tel que `.ttinclude` pour les fichiers include. Utilisez `.tt` uniquement pour les fichiers que vous souhaitez être traités comme exécution soit au moment du design des modèles de texte. Dans certains cas, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] reconnaît `.tt` fichiers et définit automatiquement leurs propriétés pour le traitement.  
  
 Commencez chaque modèle comme un prototype fixe.  
 Écrivez un exemple du code ou du texte que vous souhaitez générer et assurez-vous qu’il est correct. Puis remplacez son extension .tt et insérez incrémentielle du code qui modifie le contenu en lisant le modèle.  
  
 Envisagez d’utiliser des modèles typés.  
 Bien que vous pouvez créer un schéma XML ou de base de données pour vos modèles, il peut être utile de créer un langage spécifique du domaine (DSL). Un langage DSL présente l’avantage qu’il génère une classe pour représenter chaque nœud dans le schéma et des propriétés pour représenter les attributs. Cela signifie que vous pouvez programmer le modèle d’entreprise. Exemple :  
  
```  
Team Members:  
<# foreach (Person p in team.Members)   
 { #>   
    <#= p.Name #>   
<# } #>  
```  
  
 Envisagez d’utiliser des diagrammes pour vos modèles.  
 De nombreux modèles sont plus efficacement présentés et gérés comme des tables de texte, en particulier s’ils sont très volumineux.  
  
 Toutefois, pour certains types de besoins de l’entreprise, il est important de clarifier les jeux complexes de relations et de flux de travail et les diagrammes sont le support le mieux adapté. Le des avantages d’un diagramme sont qu’il est facile de discuter avec les utilisateurs et les autres parties prenantes. En générant du code à partir d’un modèle au niveau des besoins de l’entreprise, vous rendez votre code plus flexible lorsque les spécifications changent.  
  
 Vous pouvez également concevoir votre propre type de diagramme comme un langage spécifique à un domaine (DSL). Code peut être généré à partir d’UML et DSL. Pour plus d’informations, consultez [l’analyse et l’Architecture de modélisation](../modeling/analyze-and-model-your-architecture.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Génération de code au moment du design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)   
 [Génération de texte à l’exécution à l’aide des modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md)

