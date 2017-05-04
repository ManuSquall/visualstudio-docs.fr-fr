---
title: "Am&#233;lioration des performances d&#39;un compl&#233;ment VSTO | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 03ef25c2-6308-4737-a655-74bbbb472dc2
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Am&#233;lioration des performances d&#39;un compl&#233;ment VSTO
  Vous pouvez offrir aux utilisateurs une meilleure expérience. En effet, en optimisant les compléments VSTO que vous créez pour les applications Office, vous pouvez leur permettre d’être plus rapides pour démarrer, arrêter, ouvrir des éléments et exécuter d’autres tâches. Si vous créez un complément VSTO pour Outlook, vous pouvez également réduire les risques de désactivation du complément VSTO en raison de performances insuffisantes. Pour améliorer les performances du complément VSTO, vous pouvez implémenter les stratégies suivantes :  
  
-   [Charger les compléments VSTO à la demande](#Load)  
  
-   [Publier les solutions Office à l'aide de Windows Installer](#Publish)  
  
-   [Ignorer la réflexion du ruban](#Bypass)  
  
-   [Effectuer les opérations coûteuses dans un thread d'exécution distinct](#Perform)  
  
 Pour plus d’informations sur l’optimisation d’un complément VSTO Outlook, consultez [Critères de performances pour maintenir les compléments VSTO activés](http://go.microsoft.com/fwlink/?LinkID=266503).  
  
##  <a name="Load"></a> Charger les compléments VSTO à la demande  
 Vous pouvez configurer un complément VSTO pour qu’il se charge uniquement dans les cas suivants :  
  
-   la première fois que l’utilisateur démarre l’application après l’installation du complément VSTO ;  
  
-   la première fois que l’utilisateur interagit avec le complément VSTO après un nouveau démarrage de l’application.  
  
 Par exemple, votre complément VSTO peut remplir une feuille de calcul avec des données quand l’utilisateur choisit un bouton personnalisé appelé **Obtenir mes données**. L’application doit charger le complément VSTO au moins une fois pour que le bouton **Obtenir mes données** s’affiche dans le ruban. Toutefois, le complément VSTO ne se charge pas chaque fois que l’utilisateur démarre l’application. Il se charge uniquement quand l’utilisateur choisit le bouton **Obtenir mes données**.  
  
#### Pour configurer une solution ClickOnce visant à charger les compléments VSTO à la demande  
  
1.  Dans l'**Explorateur de solutions**, choisissez le nœud du projet.  
  
2.  Dans la barre de menus, sélectionnez **Afficher**, **Pages de propriétés**.  
  
3.  Sous l'onglet **Publier**, choisissez le bouton **Options**.  
  
4.  Dans la boîte de dialogue **Options de publication**, sélectionnez l'élément de liste **Paramètres Office**, choisissez l'option **Charger à la demande**, puis choisissez le bouton **OK**.  
  
#### Pour configurer une solution Windows Installer visant à charger les compléments VSTO à la demande  
  
1.  Dans le Registre, définissez l'entrée `LoadBehavior` de la clé *Root*\\Software\\Microsoft\\Office\\*ApplicationName*\\Addins\\*Add\-in ID* sur **0x10**.  
  
     Pour plus d'informations, consultez [Entrées de Registre pour les compléments VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
#### Pour configurer une solution visant à charger les compléments VSTO à la demande pendant le débogage de la solution  
  
1.  Créez un script qui définit l'entrée `LoadBehavior` de la clé *Root*\\Software\\Microsoft\\Office\\*ApplicationName*\\Addins\\*Add\-in ID* sur **0x10**.  
  
     Le code ci\-dessous est un exemple de ce script.  
  
    ```  
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn] "Description"="MyAddIn" "FriendlyName"="MyAddIn" "LoadBehavior"=dword:00000010 "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"  
  
    ```  
  
2.  Créez un événement post\-build qui met à jour le Registre en utilisant le script.  
  
     Le code suivant est un exemple d'une chaîne de commande que vous pouvez ajouter à un événement post\-build.  
  
    ```  
    regedit /s "$(SolutionDir)$(SolutionName).reg"  
  
    ```  
  
     Pour plus d’informations sur la création d’un événement post\-build dans un projet C\#, consultez [Comment : spécifier des événements de build &#40;C&#35;&#41;](~/ide/how-to-specify-build-events-csharp.md).  
  
     Pour plus d’informations sur la création d’un événement post\-build dans un projet Visual Basic, consultez [Comment : spécifier des événements de build &#40;C&#35;&#41;](~/ide/how-to-specify-build-events-csharp.md).  
  
##  <a name="Publish"></a> Publier des solutions Office à l'aide de Windows Installer  
 Si vous publiez votre solution à l’aide de Windows Installer, Visual Studio 2010 Tools pour Office Runtime ignore les étapes suivantes pendant le chargement du complément VSTO.  
  
-   Validation du schéma manifeste  
  
-   Recherche automatique des mises à jour  
  
-   Validation des signatures numériques des manifestes de déploiement  
  
    > [!NOTE]  
    >  Cette étape n’est pas nécessaire si vous déployez le complément VSTO à un emplacement sécurisé sur les ordinateurs des utilisateurs.  
  
 Pour plus d'informations, consultez [Déploiement d'une solution Office à l'aide de Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
##  <a name="Bypass"></a> Ignorer la réflexion du ruban  
 Si vous créez une solution à l'aide de [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], assurez\-vous que vos utilisateurs ont installé la version la plus récente de Visual Studio 2010 Tools pour Office Runtime lorsque vous déployez la solution. Les versions antérieures de ce Runtime utilisaient la réflexion dans les assemblys de la solution pour localiser les personnalisations du ruban. Ce processus peut ralentir le chargement du complément VSTO.  
  
 Sinon, vous pouvez empêcher que les versions de Visual Studio 2010 Tools pour Office Runtime utilisent la réflexion pour identifier les personnalisations du ruban. Pour suivre cette stratégie, substituez la méthode `CreateRibbonExtensibility` et retournez explicitement les objets ruban. Si votre complément VSTO ne contient pas de personnalisations de ruban, retournez `null` au sein de la méthode.  
  
 L'exemple suivant retourne un objet ruban en fonction de la valeur d'un champ.  
  
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/CS/ThisWorkbook.cs#1)]
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/VB/ThisWorkbook.vb#1)]  
  
##  <a name="Perform"></a> Effectuer les opérations coûteuses dans un thread d'exécution distinct  
 Prévoyez d'effectuer les tâches qui prennent du temps \(par exemple, les tâches longues, les connexions de base de données ou autres sortes d'appels réseau\) dans un thread distinct. Pour plus d'informations, consultez [Prise en charge des threads dans Office](../vsto/threading-support-in-office.md).  
  
> [!NOTE]  
>  Tout le code qui appelle le modèle objet Office doit s'exécuter dans le thread principal.  
  
## Voir aussi  
 [Demand\-Loading VSTO Add\-ins](http://blogs.msdn.com/b/andreww/archive/2008/07/14/demand-loading-vsto-add-ins.aspx)   
 [Delay\-loading the CLR in Office Add\-ins](http://blogs.msdn.com/b/andreww/archive/2008/04/19/delay-loading-the-clr-in-office-add-ins.aspx)   
 [VSTO Performance: Delay Loading and You \(Stephen Peters\)](http://blogs.msdn.com/b/vsto/archive/2010/01/07/vsto-performance-delay-loading-and-you.aspx)   
 [Performance Improvements Coming Soon to a Service Pack Near You \(Stephen Peters\)](http://blogs.msdn.com/b/vsto/archive/2010/11/30/performance-improvements-coming-soon-to-a-service-pack-near-you-stephen-peters.aspx)   
 [VSTO Performance: Ribbon Reflection \(Stephen Peters\)](http://blogs.msdn.com/b/vsto/archive/2010/06/03/vsto-performance-ribbon-reflection.aspx)  
  
  