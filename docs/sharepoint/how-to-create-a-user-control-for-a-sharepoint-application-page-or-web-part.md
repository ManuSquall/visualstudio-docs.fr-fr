---
title: Créer le contrôle utilisateur pour SharePoint application page ou le composant WebPart
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3a88a59e9b87a193329433e5eb0625afa1428026
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401476"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Procédure : Créer un contrôle utilisateur pour une application SharePoint partie web ou de page
  Vous pouvez créer des contrôles utilisateur personnalisés qui fournissent des fonctionnalités personnalisées pour votre solution SharePoint, et vous pouvez réutiliser cette fonctionnalité dans votre projet. Vous pouvez inclure les contrôles utilisateur dans un composant WebPart ou une application page, ajoutez d’autres contrôles ASP.NET et les contrôles de SharePoint et définir les propriétés et méthodes pour le contrôle. Pour plus d’informations sur les contrôles utilisateur, consultez [créer des contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) et [contrôles utilisateur et des contrôles serveur dans SharePoint](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/).

### <a name="to-create-a-user-control-for-sharepoint"></a>Pour créer un contrôle utilisateur pour SharePoint

1. Dans Visual Studio, ouvrez ou créez un projet SharePoint.

     Consultez [SharePoint modèles d’élément de projet et le projet](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Dans l' **Explorateur de solutions**, choisissez le nœud du projet.

3. Dans la barre de menus, choisissez **Projet** > **Ajouter un nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

4. Dans le **installé** volet, choisissez le **Office/SharePoint** nœud.

5. Dans la liste de modèles SharePoint, choisissez **contrôle utilisateur (Solution de batterie uniquement)** .

    > [!NOTE]
    > Les contrôles utilisateur fonctionnent uniquement dans les solutions de batterie de serveurs.

6. Dans le **nom** zone, spécifiez un nom pour le contrôle utilisateur, puis choisissez le **ajouter** bouton.

     Visual Studio ajoute plusieurs fichiers et dossiers à votre projet. Pour plus d’informations sur ces fichiers, consultez [créer des contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

     Par défaut, le fichier de contrôle utilisateur s’affiche dans le **Source** vue du concepteur Visual Web Developer. Dans cette vue, vous pouvez modifier le balisage XML du contrôle. Vous pouvez basculer vers **conception** afficher si vous souhaitez concevoir visuellement le contrôle en faisant glisser des contrôles à partir de la **boîte à outils**. Consultez [mode conception, le Concepteur de pages Web](/previous-versions/aspnet/ms178149\(v\=vs.100\)).

7. Si vous souhaitez gérer les événements qui se produisent dans le contrôle, ajoutez le code au fichier de code du contrôle utilisateur.

     Ce fichier s’affiche dans **l’Explorateur de solutions** sous le fichier de contrôle utilisateur et a un *.cs* ou *.vb* extension, selon le langage du projet.

## <a name="see-also"></a>Voir aussi
- [Créer des contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
- [Créer des pages d’application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
