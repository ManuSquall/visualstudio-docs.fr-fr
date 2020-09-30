---
title: Création de contrôles réutilisables pour des composants WebPart ou des pages d’application | Microsoft Docs
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d3052b2eab3dc353cdccc991a793c47485037fe8
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585091"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>Créer des contrôles réutilisables pour les composants WebPart ou les pages d’application
  Dans Visual Studio, vous pouvez créer des contrôles personnalisés et réutilisables qui peuvent être utilisés par les pages d’application et les composants WebPart qui s’exécutent dans SharePoint. Ces contrôles sont appelés contrôles utilisateur. Un contrôle utilisateur est un type de contrôle composite qui fonctionne très bien comme une page Web ASP.NET. vous pouvez ajouter des contrôles serveur Web existants et des balises à un contrôle utilisateur, et définir des propriétés et des méthodes pour le contrôle. Vous pouvez ensuite les incorporer dans des pages Web ASP.NET, où elles jouent le rôle d’unité.

## <a name="create-a-user-control"></a>Créer un contrôle utilisateur
 Pour créer un contrôle utilisateur, ajoutez un **contrôle utilisateur** à un **projet SharePoint vide**. Pour plus d’informations, consultez [Comment : créer un contrôle utilisateur pour une page d’application SharePoint ou un composant WebPart](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).

 Quand vous ajoutez un élément de **contrôle utilisateur** , Visual Studio crée un dossier dans votre projet, puis ajoute plusieurs fichiers au dossier. Le tableau suivant décrit chaque fichier.

|Fichier|Description|
|----------|-----------------|
|Fichier de contrôle utilisateur|Définit le contrôle utilisateur. Concevez le contrôle utilisateur en ajoutant des contrôles et des balises à ce fichier.|
|Fichier de code|Contient le code-behind du contrôle utilisateur. Ajoutez du code pour gérer les événements dans ce fichier.|
|Fichier de code du concepteur|Contient le code généré par le concepteur et ne doit pas être modifié directement.|

## <a name="design-the-user-control"></a>Concevoir le contrôle utilisateur
 Concevez le contrôle utilisateur à l’aide du concepteur Visual Web Developer dans Visual Studio. Ce concepteur s’affiche lorsque vous ouvrez le fichier de contrôle utilisateur dans votre projet et que vous choisissez l’onglet **conception** .

## <a name="consume-the-user-control"></a>Utiliser le contrôle utilisateur
 Les contrôles utilisateur n’apparaissent pas dans SharePoint tant que vous ne les incluez pas dans une page d’application ou un composant WebPart.

 Pour inclure un contrôle utilisateur dans une page d’application, ouvrez la page Web à laquelle vous souhaitez ajouter le contrôle utilisateur ASP.NET. Basculez vers Mode Création, puis sélectionnez votre fichier de contrôle utilisateur personnalisé dans Explorateur de solutions et faites-le glisser sur la page. Le contrôle utilisateur ASP.NET est ajouté à la page et le concepteur crée la directive @ Register, qui est nécessaire pour que la page reconnaisse le contrôle utilisateur. Vous pouvez maintenant utiliser les propriétés et les méthodes publiques du contrôle.

 Pour inclure un contrôle utilisateur dans un composant WebPart, ajoutez le contrôle utilisateur à la collection de composants WebPart <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> dans le fichier de code du composant WebPart. L’exemple suivant ajoute un contrôle utilisateur à la <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> collection d’un composant WebPart.

 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]

## <a name="debug-a-user-control"></a>Déboguer un contrôle utilisateur
 Pour déboguer un contrôle utilisateur, assurez-vous que le contrôle utilisateur est inclus dans une page d’application ou un composant WebPart dans votre projet SharePoint. Vous pouvez ensuite déboguer le code dans le contrôle utilisateur de la même façon que vous déboguez le code dans n’importe quel projet Visual Studio.

 Quand vous démarrez le débogueur Visual Studio, Visual Studio ouvre le site SharePoint.

 Dans SharePoint, ouvrez la page d’application qui comprend le contrôle utilisateur. Si le contrôle utilisateur est inclus dans un composant WebPart, ajoutez le composant WebPart à une page de composant WebPart dans SharePoint.

 Pour plus d’informations sur le débogage des projets SharePoint, consultez [résoudre les problèmes liés aux solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Comment : créer un contrôle utilisateur pour une page d’application SharePoint ou un composant WebPart](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Montre comment créer des contrôles personnalisés et réutilisables qui peuvent être utilisés par les pages d’application et les composants WebPart qui s’exécutent dans SharePoint.|
