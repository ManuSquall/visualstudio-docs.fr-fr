---
title: Générer du code à partir de diagrammes de classes UML | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates.TextTransformationDataCollectionEditor
helpviewer_keywords:
- code generation, UML class diagrams
- class diagrams - UML, generating code
- UML diagrams, generating code
ms.assetid: 2790e64d-7728-4c2e-a4dd-4131e795f730
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a8108a552f21504714fea84bcb29194db4d947cf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764767"
---
# <a name="generate-code-from-uml-class-diagrams"></a>Générer du code à partir de diagrammes de classes UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour générer le code Visual c# .NET à partir de diagrammes de classes UML dans Visual Studio, utilisez le **générer le Code** commande. Par défaut, la commande génère un type C# pour chaque type UML que vous sélectionnez. Vous pouvez modifier et étendre ce comportement en modifiant ou en copiant les modèles de texte qui génèrent le code. Vous pouvez spécifier un comportement distinct pour les types contenus dans les différents packages de votre modèle.  

 Le **générer le Code** commande est particulièrement adaptée à la génération de code à partir de la sélection de l’utilisateur d’éléments et à la génération d’un fichier pour chaque classe UML ou un autre élément. Par exemple, la capture d'écran présente deux fichiers C# générés à partir de deux classes UML.  

 Comme alternative, si vous souhaitez générer le code dans lequel les fichiers générés n’ont pas d’une relation 1:1 avec les éléments UML, vous pouvez envisager d’écrire des modèles de texte qui sont appelées avec le **transformer tous les modèles** commande. Pour plus d’informations sur cette méthode, consultez [générer des fichiers à partir d’un modèle UML](../modeling/generate-files-from-a-uml-model.md).  

 ![Diagramme et C généré de classe UML&#35; fichiers de classe. ](../modeling/media/oob-gencode1.png "oob_GenCode1")  

 Pour plus d'informations sur les diagrammes de classes UML dans Visual Studio, consultez les rubriques suivantes :  

- [Informations de référence sur les diagrammes de classes UML](../modeling/uml-class-diagrams-reference.md)  

- [Diagrammes de classes UML : recommandations](../modeling/uml-class-diagrams-guidelines.md)  

  Pour connaître les versions de Visual Studio prennent en charge les diagrammes de classes UML, consultez [versions prises en charge pour l’architecture et les outils de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  

## <a name="using-the-generate-code-command"></a>Utilisation de la commande Generate Code  
 La procédure suivante décrit le comportement par défaut de la **générer le Code** commande :  

#### <a name="to-generate-a-separate-file-for-each-element"></a>Pour générer un fichier séparé pour chaque élément  

1. Créez un modèle UML qui contient des classes. Vous pouvez appliquer des stéréotypes aux éléments de modèle.  

    Pour plus d’informations, consultez [transformations de génération de Code par défaut](#default).  

2. Sur un diagramme de classes ou dans **Explorateur de modèles UML**, sélectionner des éléments à partir de laquelle vous souhaitez générer le code. Vous pouvez sélectionner l'un des éléments suivants :  

   -   Un ensemble spécifique d'éléments.  

   -   Un package ou le modèle, pour générer le code à partir de son contenu.  

   -   Le diagramme, pour en sélectionner tous les éléments.  

3. Ouvrez le menu contextuel pour un élément sélectionné, puis choisissez **générer le Code**.  

    La première fois que vous utilisez **générer le Code** dans un modèle particulier, une boîte de dialogue s’affiche. Cette boîte de dialogue vous permet de modifier les paramètres de génération de code du modèle.  

    Choisissez **OK** , sauf si vous savez que vous souhaitez modifier ces paramètres.  

    Pour revenir ultérieurement à cette boîte de dialogue, ouvrez **Explorateur de modèles UML**. Ouvrez la modélisation menu contextuel du projet, puis choisissez **configurer la génération de Code**. Pour plus d’informations, consultez [personnalisation de la commande Generate Code](#custom).  

   Les fichiers qui contiennent le code C# sont générés. Dans le cas par défaut, un fichier est généré pour chaque type, et les fichiers sont générés dans un projet de bibliothèque de classes C#. Vous pouvez toutefois personnaliser ce comportement. Pour plus d’informations, consultez [personnalisation de la commande Generate Code](#custom).  

   Certains tests de validation sont appliqués au modèle pour vérifier qu’il peut être traduit en C#. Si ces tests échouent, un message d'erreur est affiché et la génération de code n'est pas exécutée. Si vous avez créé une commande de menu de validation, le code n’est pas généré pour tout élément pour lequel votre commande de validation échoue. Pour plus d’informations, consultez [définir des contraintes de validation pour les modèles UML](../modeling/define-validation-constraints-for-uml-models.md).  

##  <a name="default"></a> Transformations de génération de Code par défaut  
 Cette section résume les résultats produits par le **générer le Code** commande, sauf si vous personnalisez la commande. Pour plus d’informations, consultez [personnalisation de la commande Generate Code](#custom).  

- Un type C# est produit pour chaque type que vous avez sélectionné dans le modèle UML. Chaque type est placé dans un fichier de code séparé sous le **GeneratedCode** dossier.  

- Si le type UML est contenu dans un package, le type C# généré est placé à l’intérieur d’un espace de noms et le fichier est généré dans un dossier portant le même nom que l’espace de noms.  

- Une propriété C# est générée pour chaque `Attribute` d'une classe UML.  

- Une méthode C# est générée pour chaque `Operation` d'un type UML.  

- Un champ C# est généré pour chaque association navigable à laquelle la classe participe.  

  En ajoutant un stéréotype à chaque type UML, vous pouvez contrôler un plus grand nombre de propriétés du type C# généré.  

|**Pour créer ce type c#**|**Dessiner ce type UML**|**Appliquer ce stéréotype**|  
|---------------------------------|----------------------------|-------------------------------|  
|Classe|Classe|\<Aucun > ou<br /><br /> C# class|  
|Interface|Interface|\<Aucun > ou<br /><br /> C# interface|  
|Énumération|Énumération|\<Aucun > ou<br /><br /> C# enum|  
|Délégué|Classe|C# delegate|  
|Struct|Classe|C# struct|  

#### <a name="to-set-a-stereotype-on-a-type-or-other-element"></a>Pour définir un stéréotype sur un type ou un autre élément  

1. Ouvrez le menu contextuel pour l’élément sur un diagramme ou dans **Explorateur de modèles UML**, puis choisissez **propriétés**.  

2. Dans le **propriétés** fenêtre, cliquez sur la flèche déroulante dans le **stéréotypes** propriété et sélectionnez la case à cocher pour le stéréotype que vous souhaitez appliquer.  

   > [!TIP]
   >  Si les stéréotypes C# ne s'affichent pas, activez le profil C# pour le modèle ou pour un package qui contient les éléments de modèle auxquels vous vous intéressez. Sélectionnez le package ou la racine du modèle dans **Explorateur de modèles UML**. Ensuite, dans le **propriétés** fenêtre, choisissez **profil**, puis activez le profil c#.  

3. Développez le **stéréotypes** propriété pour afficher les propriétés supplémentaires que vous pouvez définir.  

   Le **Description** propriétés de types, les attributs, les opérations et les associations sont écrites dans `<summary>` commentaires dans le code généré. Les éléments de commentaire liés aux types sont écrits dans les commentaires `<remarks>`.  

## <a name="varying-the-generated-code"></a>Variation du code généré  
 Le code généré varie en fonction des propriétés de chaque type, attribut ou opération. Par exemple, si vous définissez la **Is Abstract** propriété d’une classe est true, le `abstract` mot clé s’affiche sur la classe générée. Si vous définissez la **multiplicité** d’un attribut à ** 0..\\ , puis la propriété générée aura un `IEnumerable<>` type.  

 De plus, chaque stéréotype fournit plusieurs propriétés supplémentaires que vous pouvez définir. Ces valeurs sont traduites en mots clés appropriés dans le code C#. Par exemple, si vous définissez la propriété `Is Static` sur une classe, la classe C# sera `static`.  

 Pour définir ces propriétés supplémentaires, sélectionnez la classe ou un autre élément dans le diagramme. Dans la fenêtre Propriétés, développez **stéréotypes**, puis développez le stéréotype c#, tel que **classe c#**.  Pour les classes, ces propriétés supplémentaires incluent :  

- CLR Attributes  

- Is Partial  

- Is Static  

- Is Unsafe  

- Package Visibility  

  Chaque attribut et opération dispose également de propriétés de stéréotype que vous pouvez définir. Si vous ne voyez pas les propriétés sur un nouvel attribut, exécutez **générer le Code**.  

##  <a name="custom"></a> Personnalisation de la commande Generate Code  
 Le **générer le Code** commande fonctionne en transformant vos éléments de modèle à l’aide d’un ensemble de modèles de texte. Pour plus d’informations sur les modèles de texte, consultez [génération de Code et modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md).  

 Les modèles sont spécifiés dans un ensemble de *liaisons de modèles de texte*. Une liaison de modèle de texte spécifie quel modèle doit être appliqué, où la sortie générée doit être placée et autres paramètres de la **générer le Code** commande.  

 Lorsque vous exécutez le **générer le Code** commande sur un modèle particulier, elle joint un ensemble de liaisons de modèles par défaut à la racine du modèle. Ces liaisons s’appliquent à tous les éléments du modèle.  

 Toutefois, vous pouvez effectuer des substitutions et des ajouts pour ces liaisons par défaut, en joignant vos propres liaisons à des packages, des classes ou d'autres éléments. Une liaison s'applique à tous les éléments contenus dans l'élément auquel elle est jointe. Par exemple, si vous voulez que tous les types d’un package particulier soient transformés par un ensemble de modèles différent ou soient sortis dans un dossier distinct, vous pouvez joindre des liaisons de modèles au package.  

 Pour inspecter les liaisons de modèles attachés à un élément de modèle, choisissez le bouton de sélection **[...]**  dans le **liaisons de modèles de texte** propriété dans la fenêtre Propriétés.  

 Le **générer le Code** commande applique des modèles à chaque élément de modèle que vous avez sélectionné. Pour chaque élément, l'ensemble de modèles appliqué est l'ensemble combiné des modèles joints à ses conteneurs, jusqu'à la racine du modèle incluse.  

 Si deux liaisons de modèles dans cet ensemble ont le même nom, la liaison dans le plus petit conteneur substitue celle dans le plus grand conteneur. Par exemple, la racine du modèle a une liaison avec le nom **modèle de classe**. Pour que votre propre modèle appliqué au contenu d’un package particulier, définissez votre propre liaison de modèle qui porte le nom **modèle de classe**.  

 Plusieurs modèles peuvent être appliqués à un élément de modèle. Vous pouvez générer plusieurs fichiers à partir de chaque élément de modèle.  

> [!NOTE]
>  Les liaisons jointes à la racine du modèle agissent comme des valeurs par défaut pour tous les éléments du modèle. Pour afficher ces liaisons par défaut, ouvrez **Explorateur de modèles UML**. Ouvrez le menu contextuel du projet de modélisation, puis choisissez **configurer la génération de Code**. Vous pouvez également sélectionner la racine du modèle dans l'Explorateur de modèles UML. Dans la fenêtre Propriétés, choisissez **[...]**  dans le **liaisons de modèles de texte** propriété. Les liaisons n’apparaît que si vous avez utilisé le **générer le Code** commande au moins une fois. Les liaisons de modèles ne peuvent pas être jointes à un diagramme.  

#### <a name="to-attach-text-template-bindings-to-a-package-or-other-model-element"></a>Pour joindre des liaisons de modèles de texte à un package ou à un autre élément de modèle  

1. Dans **Explorateur de modèles UML**, ouvrez le menu contextuel pour un élément de modèle, puis choisissez **propriétés**. En général, vous joignez des liaisons de modèles de texte à un package ou à la racine du modèle.  

2. Dans le **propriétés** fenêtre, choisissez le bouton de sélection (**[...]** ) dans le **liaisons de modèles de texte** propriété.  

    Le **liaisons de modèles de texte** boîte de dialogue s’affiche.  

3. Choisissez **ajouter** pour créer une nouvelle liaison de modèle de texte.  

    \- ou -  

    choisissez une liaison existante pour la modifier.  

    Chaque liaison de modèle définit la manière dont un modèle spécifié doit être appliqué à l'élément de modèle que vous avez sélectionné, et aux autres éléments de modèle qu'il contient.  

4. Dans la boîte de dialogue, définissez les propriétés de la liaison de modèle de texte.  


   |    **Property**    |                                                                                                                                                                                                                                                                                                                    **Description**                                                                                                                                                                                                                                                                                                                    |
   |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |        Name        |                                                                                                                                                                                                                                                  Nom pour cette liaison. Pour substituer une liaison héritée d'un modèle ou d'un package contenant, utilisez le même nom que la liaison à substituer.                                                                                                                                                                                                                                                  |
   |     Overwrite      |                                                                                                                                                                                                                                                                                                      Si la valeur est true, tout code existant est remplacé.                                                                                                                                                                                                                                                                                                       |
   |    Nom de la cible     | Nom du fichier généré.<br /><br /> Vous pouvez insérer des expressions dans cette chaîne comme `{Name}` ou `{Owner.Name}`. Par exemple, vous pouvez écrire : `{Owner.Name}_{Name}`. L'expression est évaluée sur l'élément de modèle. Elle peut utiliser des propriétés d'éléments, mais pas de méthodes. Pour rechercher les propriétés peuvent être utilisées, examinez les propriétés des types dans **Microsoft.VisualStudio.Uml.\\ ***. \*\*Important :* \* `{Name}` ou `{Owner.Name}` peut uniquement être utilisée dans le **nom cible** propriété. Pour modifier le nom de la classe générée, vous devez modifier le modèle. Pour plus d’informations, consultez [écriture d’un modèle de texte](#writing). |
   |    Chemin d’accès au projet    |                                                                      Spécifie le chemin d'accès au projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] qui contiendra les fichiers de sortie de la transformation. Utilisez des valeurs typées pour créer un projet. Choisissez le bouton de sélection (**[...]** ) pour sélectionner un projet existant.<br /><br /> Un projet est créé s'il n'existe pas. Il s'agit d'un projet de bibliothèque de classes C#.<br /><br /> Pour ce faire, vous devez taper le projet directement. Vous pouvez inclure des macros de variables d'environnement telles que %ProgramFiles% ou %LocalAppData%.                                                                       |
   |  Répertoire cible  |                                                                                          Dossier dans lequel le fichier cible est généré. Le chemin d'accès est relatif au dossier du projet.<br /><br /> Vous pouvez utiliser l'expression `{PackageStructure}` pour insérer un chemin d'accès qui correspond aux noms des packages contenants. La valeur par défaut est `\GeneratedCode\{PackageStructure}`. Vous pouvez également inclure des variables d'environnement telles que %TEMP% ou %HomePath%. **Important :** `{PackageStructure}` peut uniquement être utilisée dans le **répertoire cible** propriété.                                                                                          |
   | Chemin d’accès au fichier de modèle |                                                                                                                                                           Modèle qui exécutera la transformation.<br /><br /> Vous pouvez utiliser les modèles fournis ou créer le vôtre. Les modèles fournis se trouvent à l'emplacement suivant :<br /><br /> …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\                                                                                                                                                           |


5. Vous pouvez joindre à un élément le nombre de liaisons de votre choix.  

##  <a name="writing"></a> Écriture d’un modèle de texte  
 Vous pouvez écrire vos propres modèles de texte. Les modèles de texte peuvent générer un code programme ou tout autre type de fichier texte.  

 Nous vous recommandons de commencer par modifier des copies des modèles standard. Vous pouvez copier les modèles à partir des emplacements suivants :  

 …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\  

 Pour comprendre les modèles de texte, reportez-vous aux rubriques suivantes.  

- Un modèle de texte est un prototype du fichier résultant et contient à la fois le texte résultant et le code de programme qui lit le modèle. Pour plus d’informations, consultez [génération de Code et modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md).  

- Pour naviguer dans le modèle UML dans le code de programme, vous devez utiliser l'API UML. Pour plus d’informations, consultez [naviguer dans le modèle UML](../modeling/navigate-the-uml-model.md) et [référence des API pour l’extensibilité de la modélisation UML](../modeling/api-reference-for-uml-modeling-extensibility.md).  

  Pour utiliser les modèles avec le **générer le Code** commande, vous devez inclure la directive de modélisation. Exemple :  

  `<#@ Modeling ElementType="Microsoft.VisualStudio.Uml.Classes.IClass" Processor="ModelingProcessor" #>`  

  L'attribut `ElementType` définit le type d'élément UML auquel ce modèle s'applique.  

  Dans le modèle, `this` appartient à une classe temporaire qui a les propriétés suivantes :  

- `Element` = <xref:Microsoft.VisualStudio.Uml.Classes.IElement> UML auquel le modèle est appliqué.  

- `Errors`: <xref:System.CodeDom.Compiler.CompilerErrorCollection>  

- `Host`: <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  

- `ModelBus`: <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>. Pour plus d’informations, consultez [intégrer des modèles UML avec d’autres modèles et outils](../modeling/integrate-uml-models-with-other-models-and-tools.md).  

- `ProfileName` = "C#Profile"  

- `ServiceProvider`: <xref:System.IServiceProvider>  

- `Session`: <xref:Microsoft.VisualStudio.TextTemplating.TextTemplatingSession>.  

- `Store`: <xref:Microsoft.VisualStudio.Modeling.Store>. Il s'agit du magasin du Kit de développement logiciel (SDK) Visualization and Modeling sur lequel ModelStore UML est implémenté. Pour obtenir le <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore> UML, utilisez `this.Element.GetModelStore()`.  

  Les points suivants peuvent vous être utiles lorsque vous écrivez un modèle de texte. Ces informations sont décrites en détail dans [génération de Code et modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md).  

- Vous pouvez définir l’extension de nom de fichier du résultat dans la directive `Output`. Une directive `Output` est obligatoire dans chaque modèle de texte.  

- Certains assemblys sont référencés automatiquement par le modèle. Ces assemblys incluent par exemple System.dll et Microsoft.VisualStudio.Uml.Interfaces.dll.  

   Pour utiliser d'autres assemblys dans votre code de programme de génération, vous devez utiliser une directive `Assembly`. Par exemple :  

   `<#@ Assembly Name="%ProgramFiles%\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll" #>`  

- Certains espaces de noms tels que `System` sont importés automatiquement dans votre code de programme. Pour d'autres espaces de noms, vous pouvez utiliser la directive `Import` de la même manière que vous utiliseriez une instruction `using`. Par exemple :  

   `<#@ Import Namespace="Microsoft.VisualStudio.Uml.Classes" #>`  

   `<#@ Import Namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>`  

- Utilisez la directive `Include` pour référencer le texte d'un autre fichier.  

- Les parties du modèle placées entre crochets `<# ... #>` sont exécutés par le **générer le Code** commande. Les parties du modèle à l'extérieur de ces crochets sont copiées vers le fichier de résultats. Il est important de distinguer le code de génération et le texte généré. Le texte peut être généré dans n'importe quel langage.  

- `<#= Expressions #>` sont évaluées et converties en chaînes.  

## <a name="see-also"></a>Voir aussi  
 [Diagrammes de classes UML : référence](../modeling/uml-class-diagrams-reference.md)   
 [Diagrammes de classes UML : indications](../modeling/uml-class-diagrams-guidelines.md)   
 [Générer des fichiers à partir d’un modèle UML](../modeling/generate-files-from-a-uml-model.md)



