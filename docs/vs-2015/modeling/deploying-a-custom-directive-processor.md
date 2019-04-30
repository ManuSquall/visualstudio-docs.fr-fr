---
title: Déploiement d’un processeur de Directive personnalisé | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
ms.assetid: 80c28722-a630-47b5-923b-024dc3f2c940
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c485209f47e2d119fe469a59fe379f7cabe03813
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422587"
---
# <a name="deploying-a-custom-directive-processor"></a>Déploiement d'un processeur de directive personnalisé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour utiliser un processeur de directive personnalisé dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sur n'importe quel ordinateur, vous devez l'inscrire au moyen de l'une des méthodes décrites dans cette rubrique.  
  
 Les différentes méthodes disponibles sont les suivantes :  
  
- [Extension de Visual Studio (VSIX)](http://msdn.microsoft.com/64ff1452-f7d5-42d9-98b8-76f769f76832). Cette extension permet d'installer et de désinstaller le processeur de directive sur votre propre ordinateur et sur d'autres. En général, vous pouvez empaqueter d'autres fonctionnalités dans la même extension VSIX.  
  
- [VSPackage](../extensibility/internals/vspackages.md). Si vous définissez un VSPackage qui contient d'autres fonctionnalités en plus du processeur de directive, vous pouvez aisément inscrire ce dernier.  
  
- Définition d'une clé de Registre. Dans cette méthode, vous ajoutez une entrée de Registre pour le processeur de directive.  
  
  Vous devez utiliser l'une de ces méthodes uniquement si vous voulez transformer votre modèle de texte dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Si vous employez un hôte personnalisé dans votre propre application, celui-ci est chargé de rechercher les processeurs de directive pour chaque directive.  
  
## <a name="deploying-a-directive-processor-in-a-vsix"></a>Déploiement d'un processeur de directive dans une extension VSIX  
 Vous pouvez ajouter un processeur de directive personnalisé à un [Extension Visual Studio (VSIX)](http://msdn.microsoft.com/64ff1452-f7d5-42d9-98b8-76f769f76832).  
  
 Vous devez vérifier que les deux éléments suivants figurent dans le fichier .vsix :  
  
- L'assembly (.dll) qui contient la classe du processeur de directive personnalisé.  
  
- Un fichier .pkgdef qui inscrit le processeur de directive. Le nom racine du fichier doit être identique à celui de l'assembly. Par exemple, vos fichiers peuvent être nommés CDP.dll et CDP.pkgdef.  
  
  Pour inspecter ou modifier le contenu d'un fichier .vsix, remplacez son extension de nom par .zip, puis ouvrez-le. Après avoir modifié le contenu, réaffectez l'extension .vsix au nom de fichier.  
  
  Un fichier .vsix peut être créé de plusieurs façons. La procédure suivante décrit une de ces méthodes.  
  
#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>Pour développer un processeur de directive personnalisé dans un projet VSIX  
  
1. Créez un projet VSIX dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
    - Dans le **nouveau projet** boîte de dialogue, développez **Visual Basic** ou **Visual C#**, puis développez **extensibilité**. Cliquez sur **projet VSIX**.  
  
2. Dans **source.extension.vsixmanifest**, définissez le type de contenu et les éditions prises en charge.  
  
    1. Dans l’extension VSIX, l’éditeur de manifeste sur le **actifs** , choisir **New** et définissez les propriétés du nouvel élément :  
  
         **Type de contenu** = **VSPackage**  
  
         **Projet source** = \<*le projet actuel*>  
  
    2. Cliquez sur **éditions sélectionnées** et vérifiez les types d’installation sur lequel vous souhaitez que le processeur de directive pour être utilisable.  
  
3. Ajoutez un fichier .pkgdef et définissez ses propriétés de sorte qu'il soit inclus dans l'extension VSIX.  
  
    1. Créez un fichier texte et nommez-le \< *assemblyName*> .pkgdef.  
  
         \<*assemblyName*> est généralement le même que le nom du projet.  
  
    2. Sélectionnez-le dans l'Explorateur de solutions et définissez ses propriétés comme suit :  
  
         **Action de génération** = **contenu**  
  
         **Copy to Output Directory** = **toujours copier**  
  
         **Inclure dans VSIX** = **True**  
  
    3. Définissez le nom de l'extension VSIX et assurez-vous que l'ID est unique.  
  
4. Ajoutez le texte suivant au fichier .pkgdef.  
  
    ```  
    [$RootKey$\TextTemplating]  
    [$RootKey$\TextTemplating\DirectiveProcessors]  
    [$RootKey$\TextTemplating\DirectiveProcessors\ CustomDirectiveProcessorName]  
    @="Custom Directive Processor description"  
    "Class"="NamespaceName.ClassName"  
    "CodeBase"="$PackageFolder$\AssemblyName.dll"  
    ```  
  
     Remplacez les noms suivants par vos propres noms : `CustomDirectiveProcessorName`, `NamespaceName`, `ClassName`, `AssemblyName`.  
  
5. Ajoutez les références suivantes au projet :  
  
    - **Microsoft.VisualStudio.TextTemplating.\*.0**  
  
    - **Microsoft.VisualStudio.TextTemplating.Interfaces.\*.0**  
  
    - **Microsoft.VisualStudio.TextTemplating.VSHost.\*.0**  
  
6. Ajoutez la classe de votre processeur de directive personnalisé au projet.  
  
     Il s'agit d'une classe publique qui doit implémenter <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> ou <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.  
  
#### <a name="to-install-the-custom-directive-processor"></a>Pour installer le processeur de directive Personnalisé  
  
1. Dans l’Explorateur Windows (Explorateur de fichiers dans Windows 8), ouvrez le répertoire de build (en général, bin\Debug ou bin\Release).  
  
2. Si vous voulez installer le processeur de directive sur un autre ordinateur, copiez sur ce dernier le fichier .vsix.  
  
3. Double-cliquez sur le fichier .vsix. Le programme d'installation des extensions [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] apparaît.  
  
4. Redémarrez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Vous pourrez désormais exécuter des modèles de texte qui contiennent des directives faisant référence au processeur de directive personnalisé. Chaque directive se présente comme suit :  
  
     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" … #>`  
  
#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>Pour désinstaller ou temporairement désactiver le processeur de directive personnalisé  
  
1. Dans le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **outils** menu, cliquez sur **Gestionnaire d’extensions**.  
  
2. Sélectionnez l’extension VSIX qui contient le processeur de directive, puis cliquez sur **désinstallation** ou **désactiver**.  
  
### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>Dépannage d'un processeur de directive dans une extension VSIX  
 Si le processeur de directive ne fonctionne pas, les suggestions suivantes peuvent vous aider :  
  
- Le nom de processeur que vous spécifiez dans la directive personnalisée doit correspondre à la valeur `CustomDirectiveProcessorName` que vous avez indiquée dans le fichier .pkgdef.  
  
- Votre méthode `IsDirectiveSupported` doit retourner la valeur `true` lorsque le nom de votre `CustomDirective` lui est passé.  
  
- Si vous ne voyez pas l’extension dans le Gestionnaire d’extensions, mais le système vous autorisera pas à installer, supprimez-la de **%localappdata%\Microsoft\VisualStudio\\\*. 0\Extensions\\** .  
  
- Ouvrez le fichier .vsix et inspectez son contenu. Pour l'ouvrir, remplacez l'extension de nom du fichier par .zip. Vérifiez qu'il contient les fichiers .dll, .pkgdef et extension.vsixmanifest. Le fichier extension.vsixmanifest doit comporter la liste appropriée dans le nœud SupportedProducts, ainsi qu'un nœud VsPackage sous le nœud de contenu :  
  
     `<Content>`  
  
     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`  
  
     `</Content>`  
  
## <a name="deploying-a-directive-processor-in-a-vspackage"></a>Déploiement d'un processeur de directive dans un VSPackage  
 Si votre processeur de directive fait partie d'un VSPackage qui sera installé dans le GAC, vous pouvez faire en sorte que le système génère le fichier .pkgdef à votre place.  
  
 Placez l'attribut suivant sur la classe de votre package :  
  
```  
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]  
```  
  
> [!NOTE]
> Cet attribut est placé sur la classe du package, et non pas sur la classe du processeur de directive.  
  
 Le fichier .pkgdef sera généré en même temps que le projet. Lorsque vous installerez le VSPackage, le fichier .pkgdef inscrira le processeur de directive.  
  
 Vérifiez que le fichier .pkgdef s'affiche dans le dossier de génération, qui correspond en général à bin\Debug ou bin\Release. S'il ne s'affiche pas, ouvrez le fichier .csproj dans un éditeur de texte et supprimez le nœud suivant : `<GeneratePkgDefFile>false</GeneratePkgDefFile>`.  
  
 Pour plus d'informations, consultez [VSPackages](../extensibility/internals/vspackages.md).  
  
## <a name="setting-a-registry-key"></a>Définition d'une clé de Registre  
 Cette méthode d'installation d'un processeur de directive personnalisé est la moins recommandée. Elle ne permet pas d'activer ni de désactiver facilement le processeur de directive, et ne fournit pas de méthode pour distribuer le processeur de directive aux autres utilisateurs.  
  
> [!CAUTION]
> Une modification incorrecte du Registre peut endommager gravement votre système. Avant d'apporter des modifications au Registre, veillez à sauvegarder toutes les données importantes qui se trouvent sur l'ordinateur.  
  
#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>Pour inscrire un processeur de directive en définissant une clé de Registre  
  
1. Exécutez `regedit`.  
  
2. Dans regedit, accédez à  
  
    **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**  
  
    Si vous voulez installer le processeur de directive dans la version expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], insérez "Exp" après "11.0".  
  
3. Ajoutez une clé de Registre ayant le même nom que la classe du processeur de directive.  
  
   - Dans l’arborescence du Registre, cliquez sur le **DirectiveProcessors** nœud, pointez sur **New**, puis cliquez sur **clé**.  
  
4. Dans le nouveau nœud, ajoutez des valeurs de chaîne pour Class, CodeBase ou Assembly, en fonction des tableaux suivants.  
  
   1. Cliquez sur le nœud que vous avez créé, pointez sur **New**, puis cliquez sur **valeur de chaîne**.  
  
   2. Modifiez le nom de la valeur.  
  
   3. Double-cliquez sur le nom et modifiez les données.  
  
   Si le processeur de directive personnalisé ne se trouve pas dans le GAC, les sous-clés de Registre doivent se présenter comme dans le tableau suivant :  
  
|Nom|Type|Données|  
|----------|----------|----------|  
|(Default)|REG_SZ|(valeur non définie)|  
|Classe|REG_SZ|**\<Nom de Namespace >. \<Nom de la classe >**|  
|CodeBase|REG_SZ|**\<Votre chemin d’accès >\\< votre nom de l’Assembly\>**|  
  
 Si l'assembly se trouve dans le GAC, les sous-clés de Registre doivent se présenter comme dans le tableau suivant :  
  
|Nom|Type|Données|  
|----------|----------|----------|  
|(Default)|REG_SZ|(valeur non définie)|  
|Classe|REG_SZ|\<**Votre nom de classe complet**>|  
|Assembly|REG_SZ|\<**Votre nom de l’Assembly dans le GAC**>|  
  
## <a name="see-also"></a>Voir aussi  
 [Création de processeurs de directives de modèles de texte T4 personnalisés](../modeling/creating-custom-t4-text-template-directive-processors.md)
