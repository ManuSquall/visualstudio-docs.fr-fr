---
title: "Amélioration des performances d’un complément VSTO | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 03ef25c2-6308-4737-a655-74bbbb472dc2
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: bafc82f247f067f1f836730ec1f676f2f9559915
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="improving-the-performance-of-a-vsto-add-in"></a>Amélioration des performances d'un complément VSTO
  Vous pouvez offrir aux utilisateurs une meilleure expérience. En effet, en optimisant les compléments VSTO que vous créez pour les applications Office, vous pouvez leur permettre d’être plus rapides pour démarrer, arrêter, ouvrir des éléments et exécuter d’autres tâches. Si vous créez un complément VSTO pour Outlook, vous pouvez également réduire les risques de désactivation du complément VSTO en raison de performances insuffisantes. Pour améliorer les performances du complément VSTO, vous pouvez implémenter les stratégies suivantes :  
  
-   [Charger les compléments VSTO à la demande](#Load)  
  
-   [Publier les solutions Office à l'aide de Windows Installer](#Publish)  
  
-   [Ignorer la réflexion du ruban](#Bypass)  
  
-   [Effectuer les opérations coûteuses dans un thread d'exécution distinct](#Perform)  
  
 Pour plus d’informations sur l’optimisation d’un complément VSTO Outlook, consultez [Critères de performances pour maintenir les compléments VSTO activés](http://go.microsoft.com/fwlink/?LinkID=266503).  
  
##  <a name="Load"></a> Charger les compléments VSTO à la demande  
 Vous pouvez configurer un complément VSTO pour qu’il se charge uniquement dans les cas suivants :  
  
-   la première fois que l’utilisateur démarre l’application après l’installation du complément VSTO ;  
  
-   la première fois que l’utilisateur interagit avec le complément VSTO après un nouveau démarrage de l’application.  
  
 Par exemple, votre composant complément VSTO peut remplir une feuille de calcul avec des données lorsque l’utilisateur choisit un bouton personnalisé qui porte le nom **obtenir mes données**. L’application doit charger le complément VSTO au moins une fois pour que le bouton **Obtenir mes données** s’affiche dans le ruban. Toutefois, le composant logiciel complément VSTO n’est pas chargé à nouveau lorsque l’utilisateur démarre l’application de la prochaine fois. Il se charge uniquement quand l’utilisateur choisit le bouton **Obtenir mes données** .  
  
#### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Pour configurer une solution ClickOnce visant à charger les compléments VSTO à la demande  
  
1.  Dans l' **Explorateur de solutions**, choisissez le nœud du projet.  
  
2.  Dans la barre de menus, sélectionnez **Afficher**, **Pages de propriétés**.  
  
3.  Sous l'onglet **Publier** , choisissez le bouton **Options** .  
  
4.  Dans la boîte de dialogue **Options de publication** , sélectionnez l'élément de liste **Paramètres Office** , choisissez l'option **Charger à la demande** , puis choisissez le bouton **OK** .  
  
#### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Pour configurer une solution Windows Installer visant à charger les compléments VSTO à la demande  
  
1.  Dans le Registre, définissez la `LoadBehavior` entrée de la *racine*\Software\Microsoft\Office\\*ApplicationName*\Addins\\*Add-in ID*clé **0 x 10**.  
  
     Pour plus d'informations, consultez [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).  
  
#### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Pour configurer une solution visant à charger les compléments VSTO à la demande pendant le débogage de la solution  
  
1.  Créer un script qui définit le `LoadBehavior` entrée de la *racine*\Software\Microsoft\Office\\*ApplicationName*\Addins\\*Add-in ID* clé **0 x 10**.  
  
     Le code ci-dessous est un exemple de ce script.  
  
    ```  
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]  
    "Description"="MyAddIn"  
    "FriendlyName"="MyAddIn"  
    "LoadBehavior"=dword:00000010  
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"  
  
    ```  
  
2.  Créez un événement post-build qui met à jour le Registre en utilisant le script.  
  
     Le code suivant est un exemple d'une chaîne de commande que vous pouvez ajouter à un événement post-build.  
  
    ```  
    regedit /s "$(SolutionDir)$(SolutionName).reg"  
  
    ```  
  
     Pour plus d’informations sur la façon de créer un événement post-build dans un projet c#, consultez [Comment : spécifier des événements de Build &#40; C &#35; &#41; ](/visualstudio/ide/how-to-specify-build-events-csharp).  
  
     Pour plus d’informations sur la création d’un événement post-build dans un projet Visual Basic, consultez [Comment : spécifier des événements de Build &#40; Visual Basic &#41; ](/visualstudio/ide/how-to-specify-build-events-visual-basic).  
  
##  <a name="Publish"></a> Publish Office Solutions by Using Windows Installer  
 Si vous publiez votre solution à l’aide de Windows Installer, Visual Studio 2010 Tools pour Office Runtime ignore les étapes suivantes pendant le chargement du complément VSTO.  
  
-   Validation du schéma manifeste  
  
-   Recherche automatique des mises à jour  
  
-   Validation des signatures numériques des manifestes de déploiement  
  
    > [!NOTE]  
    >  Cette approche n’est pas nécessaire si vous déployez votre complément, VSTO à un emplacement sécurisé sur les ordinateurs des utilisateurs.  
  
 Pour plus d'informations, consultez [Deploying an Office Solution by Using Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
##  <a name="Bypass"></a> Bypass Ribbon Reflection  
 Si vous créez une solution à l'aide de [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], assurez-vous que vos utilisateurs ont installé la version la plus récente de Visual Studio 2010 Tools pour Office Runtime lorsque vous déployez la solution. Les versions antérieures de ce Runtime utilisaient la réflexion dans les assemblys de la solution pour localiser les personnalisations du ruban. Ce processus peut ralentir le chargement du complément VSTO.  
  
 Sinon, vous pouvez empêcher que les versions de Visual Studio 2010 Tools pour Office Runtime utilisent la réflexion pour identifier les personnalisations du ruban. Pour suivre cette stratégie, substituez la méthode `CreateRibbonExtensibility` et retournez explicitement les objets ruban. Si votre composant complément VSTO ne contient pas toutes les personnalisations de ruban, retourner `null` au sein de la méthode.  
  
 L'exemple suivant retourne un objet ruban en fonction de la valeur d'un champ.  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]  
  
##  <a name="Perform"></a> Perform Expensive Operations in a Separate Execution Thread  
 Prévoyez d'effectuer les tâches qui prennent du temps (par exemple, les tâches longues, les connexions de base de données ou autres sortes d'appels réseau) dans un thread distinct. Pour plus d'informations, consultez [Threading Support in Office](../vsto/threading-support-in-office.md).  
  
> [!NOTE]  
>  Tout le code qui appelle le modèle objet Office doit s'exécuter dans le thread principal.  
  
## <a name="see-also"></a>Voir aussi  
 [Demand-Loading VSTO Add-ins](http://blogs.msdn.com/b/andreww/archive/2008/07/14/demand-loading-vsto-add-ins.aspx)   
 [Délai de chargement CLR dans des compléments Office](http://blogs.msdn.com/b/andreww/archive/2008/04/19/delay-loading-the-clr-in-office-add-ins.aspx)   
 [Performances de VSTO : Chargement différé et vous (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/01/07/vsto-performance-delay-loading-and-you.aspx)   
 [Améliorations des performances sera bientôt disponible pour un Service Pack près de chez vous (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/11/30/performance-improvements-coming-soon-to-a-service-pack-near-you-stephen-peters.aspx)   
 [VSTO performances : La réflexion du ruban (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/06/03/vsto-performance-ribbon-reflection.aspx)  
  
  