---
title: Utilisation de modules pour inclure des fichiers dans la solution | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f8f2aa6c5d86af2424a811b6167829cefdb6fb5
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985295"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Utiliser des modules pour inclure des fichiers dans la solution
  Il peut arriver que vous souhaitiez déployer des fichiers sur le serveur SharePoint, quel que soit leur type de fichier, par exemple les nouvelles pages maîtres. Pour ce faire, vous pouvez utiliser des *modules* (à ne pas confondre avec les modules de code [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]). Les modules sont des conteneurs de fichiers dans une solution SharePoint. Lorsque la solution est déployée, les fichiers du module sont copiés dans les dossiers spécifiés sur le serveur SharePoint.

## <a name="module-items-and-elements"></a>Éléments et éléments de module
 Pour créer un module, ajoutez-le à un projet en le sélectionnant dans la boîte de dialogue **Ajouter un nouvel élément** . Ensuite, modifiez son fichier *Elements. xml* de façon à inclure les noms des fichiers que vous souhaitez déployer, où ils se trouvent sur le système, et où ils doivent être copiés sur le serveur SharePoint.

 Voici un exemple de fichier *Elements. xml* pour un module :

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 Les modules nouvellement créés contiennent les fichiers par défaut suivants :

|Nom du fichier|Description|
|---------------|-----------------|
|*Éléments. Xml*|Fichier de définition du module.|
|*Sample. txt*|Fichier d’espace réservé qui sert d’exemple de fichier dans le module.|

 Le fichier *Elements. xml* contient les éléments suivants :

|Nom de l'élément|Description|
|------------------|-----------------|
|Éléments|Contient tous les éléments définis dans le module.|
|Module|L’élément module possède un attribut unique, *Name*, qui spécifie le nom du module au format `<Module Name="Module1">`.<br /><br /> Notez que si vous modifiez le nom du module (ou sa propriété *nom de dossier* ), vous devez mettre à jour manuellement le nom dans l’élément de module.<br /><br /> Si vous spécifiez un sous-répertoire pour le ou les fichiers dans l’élément de module, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) crée automatiquement une structure de répertoire correspondante.|
|Fichier|L’élément file a deux paramètres, *path* et *URL*.<br /><br /> -Path : nom et emplacement du fichier dans la solution SharePoint. Le format est, `Path="Module1\Sample.txt"`.<br /><br /> -URL : emplacement où le fichier sera déployé sur le serveur SharePoint. Le format est, `Url="Module1/Sample.txt"`.<br /><br /> -Type : attribut facultatif qui a deux paramètres : *GhostableInLibrary* et *Ghostable*. Le format est, `Type="GhostableInLibrary"`. La spécification de *GhostableInLibrary* signifie que le fichier sera ajouté à une bibliothèque de documents dans SharePoint avec un élément de liste pour accompagner le fichier lorsqu’il est ajouté à la bibliothèque. Si vous spécifiez *Ghostable* , le fichier est ajouté à SharePoint en dehors de la bibliothèque de documents.|

 Chaque fichier que vous souhaitez déployer requiert une entrée d’élément `<File>` distincte dans *Elements. xml*.

## <a name="see-also"></a>Voir aussi
- [Comment : inclure des fichiers à l’aide d’un module](../sharepoint/how-to-include-files-by-using-a-module.md)
- [Comment : approvisionner un fichier](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [Développement de solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
