---
title: "Deploying COM Components with ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "registration-free COM deployment"
  - "ClickOnce deployment, COM components"
  - "COM components, deploying"
  - "deploying applications [ClickOnce], COM components"
  - "components, deploying"
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# Deploying COM Components with ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le déploiement de composants COM hérités \(legacy\) représentait jusqu'ici une tâche difficile.  Les composants doivent être inscrits globalement et peuvent donc entraîner des effets secondaires indésirables entre des applications qui utilisent des composants partagés.  Cette situation ne pose généralement pas de problème dans les applications du .NET Framework, car les composants sont complètement isolés de l'application ou sont compatibles côte à côte.  Visual Studio vous permet de déployer des composants COM isolés sur un système d'exploitation Windows XP ou supérieur.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fournit un mécanisme simple et sécurisé pour le déploiement de vos applications .NET.  Toutefois, si vos applications utilisent des composants COM hérités \(legacy\), vous devrez prendre des mesures supplémentaires pour les déployer.  Cette rubrique décrit comment déployer des composants COM isolés et référencer des composants natifs \(par exemple, de Visual Basic 6.0 ou Visual C\+\+\).  
  
 Pour plus d'informations sur le déploiement de composants COM isolés, consultez « Simplify App Deployment with [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] and Registration\-Free COM » à l'adresse suivante : [http:\/\/msdn.microsoft.com\/msdnmag\/issues\/05\/04\/RegFreeCOM\/default.aspx](http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx).  
  
## COM sans inscription  
 COM sans inscription est une nouvelle technologie de déploiement et d'activation de composants COM isolés.  Plutôt que de placer toutes les informations relatives à l'inscription et aux bibliothèques de types des composants dans la base de registres, cette technologie les place dans un fichier XML appelé manifeste, stocké dans le même dossier que l'application.  
  
 L'isolation d'un composant COM exige qu'il soit inscrit sur l'ordinateur du développeur, mais pas nécessairement sur celui de l'utilisateur final.  Pour isoler un composant COM, il vous suffit d'affecter à la propriété **Isolated** de sa référence la valeur **True**.  Par défaut, cette propriété a la valeur **False**, ce qui indique qu'il doit être traité comme une référence COM inscrite.  Si cette propriété a la valeur **True**, cela provoque la création d'un manifeste pour ce composant au moment de sa génération.  Cela entraîne également la copie des fichiers correspondants dans le dossier de l'application pendant l'installation.  
  
 Lorsque le générateur de manifeste rencontre une référence COM isolée, il énumère toutes les entrées `CoClass` contenues dans la bibliothèque de types du composant, en faisant correspondre chaque entrée aux données d'inscription associées, et en générant des définitions de manifeste pour toutes les classes COM contenues dans le fichier de bibliothèque de types.  
  
## Déploiement de composants COM sans inscription à l'aide de ClickOnce  
 La technologie de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est bien adaptée au déploiement de composants COM isolés, car [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] et COM sans inscription exigent tous deux qu'un composant ait un manifeste pour être déployé.  
  
 En général, l'auteur du composant doit fournir un manifeste.  Toutefois, si ce n'est pas le cas, Visual Studio est capable de générer automatiquement un manifeste pour un composant COM.  La génération d'un manifeste s'effectue pendant le processus de publication [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ; pour plus d'informations, consultez [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md).  Cette fonctionnalité vous permet également de bénéficier de composants hérités \(legacy\) que vous avez créés dans des environnements de développement antérieurs, tels que Visual Basic 6.0.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] peut déployer des composants COM de deux manières :  
  
-   Utilisation du programme d'amorçage pour déployer vos composants COM ; cela fonctionne sur toutes les plateformes prises en charge.  
  
-   Utilisation de l'isolation des composants natifs \(également connue sous le nom de déploiement COM sans inscription\).  Toutefois, cela ne fonctionne que sur un système d'exploitation Windows XP ou supérieur.  
  
### Exemple d'isolation et de déploiement d'un composant COM simple  
 Pour montrer le déploiement d'un composant COM sans inscription, cet exemple crée une application Windows en Visual Basic, qui fait référence à un composant COM natif isolé créé à l'aide de Visual Basic 6.0 et la déploie à l'aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Vous devez d'abord créer le composant COM natif:  
  
##### Pour créer un composant COM natif  
  
1.  Dans le menu **Fichier** de Visual Basic 6.0, cliquez sur **Nouveau**, puis sur **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, sélectionnez le nœud **Visual Basic** et sélectionnez un projet **ActiveX DLL**.  Dans la zone **Nom**, tapez `VB6Hello`.  
  
    > [!NOTE]
    >  Seuls les types de projets DLL ActiveX et Contrôle ActiveX sont pris en charge avec COM sans inscription ; les types de projets EXE ActiveX et Document ActiveX ne sont pas pris en charge.  
  
3.  Dans l'**Explorateur de solutions**, double\-cliquez sur **Class1.vb** pour ouvrir l'éditeur de texte.  
  
4.  Dans Class1.vb, ajoutez le code suivant après le code généré pour la méthode `New` :  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  Générez le composant.  Dans le menu **Générer**, cliquez sur **Générer la solution**.  
  
> [!NOTE]
>  COM sans inscription ne prend en charge que les types de projets de DLL et de contrôles COM.  Vous ne pouvez pas utiliser de fichiers EXE avec COM sans inscription.  
  
 Vous pouvez désormais créer une application Windows et y ajouter une référence au composant COM.  
  
##### Pour créer une application Windows à l'aide d'un composant COM  
  
1.  Dans le menu **Fichier** de Visual Basic, cliquez sur **Nouveau**, puis sur **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, sélectionnez le nœud **Visual Basic** et sélectionnez **Application Windows**.  Dans la zone **Nom**, tapez `RegFreeComDemo`.  
  
3.  Dans l'**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers** pour afficher les références de projet.  
  
4.  Cliquez avec le bouton droit sur le nœud **Références** et sélectionnez **Ajouter une référence** dans le menu contextuel.  
  
5.  Dans la boîte de dialogue **Ajouter une référence**, cliquez sur l'onglet **Parcourir**, naviguez jusqu'au fichier VB6Hello.dll, puis sélectionnez\-le.  
  
     Une référence **VB6Hello** apparaît dans la liste de références.  
  
6.  Pointez sur la **boîte à outils**, sélectionnez un contrôle **Button** et faites\-le glisser jusqu'au formulaire **Form1**.  
  
7.  Dans la fenêtre **Propriétés**, affectez à la propriété **Text** du bouton la valeur Hello.  
  
8.  Double\-cliquez sur le bouton pour ajouter le code du gestionnaire, puis dans le fichier de code, ajoutez du code afin que le gestionnaire lise les informations suivantes :  
  
    ```  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
        Dim VbObj As New VB6Hello.Class1  
        VbObj.SayHello()  
    End Sub  
    ```  
  
9. Exécutez l'application.  Dans le menu **Déboguer**, cliquez sur **Démarrer le débogage**.  
  
 Ensuite, vous devez isoler le contrôle.  Chaque composant COM que votre application utilise est représenté dans votre projet sous la forme d'une référence COM.  Ces références sont visibles sous le nœud **Références** de la fenêtre **Explorateur de solutions**.  \(Remarquez que vous pouvez ajouter des références directement à l'aide de la commande **Ajouter une référence** du menu **Projet** ou indirectement en faisant glisser un composant ActiveX jusqu'à votre formulaire.\)  
  
 La procédure suivante montre comment isoler le COM composant et publier l'application mise à jour qui contient le contrôle isolé :  
  
##### Pour isoler un composant COM  
  
1.  Dans le nœud **Références** de l'**Explorateur de solutions**, sélectionnez la référence **VB6Hello**.  
  
2.  Dans la fenêtre **Propriétés**, remplacez la valeur de la propriété **Isolated** \(**False**\) par **True**.  
  
3.  Dans le menu **Générer**, cliquez sur **Générer la solution**.  
  
 Désormais, lorsque vous appuyez sur F5, l'application fonctionne de la manière escomptée, mais elle s'exécute à présent sous COM sans inscription.  Pour preuve, essayez d'annuler l'inscription du composant VB6Hello.dll et d'exécuter RegFreeComDemo1.exe en dehors de l'IDE de Visual Studio.  Cette fois, lorsque vous cliquez sur le bouton, il fonctionne toujours.  Si vous renommez temporairement le manifeste d'application, il échoue à nouveau.  
  
> [!NOTE]
>  Vous pouvez simuler l'absence d'un composant COM en annulant temporairement son enregistrement.  Ouvrez une invite de commandes, accédez à votre dossier système en tapant `cd /d %windir%\system32`, puis annulez l'inscription du composant en tapant `regsvr32 /u VB6Hello.dll`.  Vous pouvez l'inscrire à nouveau en tapant `regsvr32 VB6Hello.dll`.  
  
 La dernière étape consiste à publier l'application à l'aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] :  
  
##### Pour publier une mise à jour d'application avec un composant COM isolé  
  
1.  Dans le menu **Générer**, cliquez sur **Publier RegFreeComDemo**.  
  
     L'Assistant Publication s'affiche.  
  
2.  Dans l'Assistant Publication, spécifiez un emplacement sur le disque de l'ordinateur local auquel vous pouvez accéder et examinez les fichiers publiés.  
  
3.  Cliquez sur **Terminer** pour publier l'application.  
  
 Si vous examinez les fichiers publiés, vous pouvez constater que le fichier sysmon.ocx est inclus.  Le contrôle est totalement isolé de cette application, ce qui signifie que si l'ordinateur de l'utilisateur final possède une autre application utilisant une autre version du contrôle, elle ne peut pas interférer avec cette application.  
  
## Référencer des assemblys natifs  
 Visual Studio prend en charge les références à des assemblys Visual Basic 6.0 ou C\+\+ natifs ; ce type de références porte le nom de références natives.  Vous pouvez déterminer si une référence est native en vérifiant que sa propriété **File Type** a la valeur **Native** ou **ActiveX**.  
  
 Pour ajouter une référence native, utilisez la commande **Ajouter une référence**, puis naviguez jusqu'au manifeste.  Certains composants placent le manifeste à l'intérieur de la DLL.  Dans ce cas, il vous suffit de choisir la DLL proprement dite et Visual Studio l'ajoutera comme référence native s'il détecte que le composant contient un manifeste incorporé.  Visual Studio inclura aussi automatiquement tous les fichiers ou les assemblys dépendants répertoriés dans le manifeste s'ils se trouvent dans le même dossier que le composant référencé.  
  
 L'isolation d'un contrôle COM facilite le déploiement des composants COM qui ne possèdent pas encore de manifeste.  Toutefois, si un composant est fourni avec un manifeste, vous pouvez référencer directement le manifeste.  En réalité, il est toujours conseillé d'utiliser le manifeste fourni par l'auteur du composant dans la mesure du possible plutôt que d'utiliser la propriété **Isolated**.  
  
## Limitations du déploiement de composants COM sans inscription  
 COM sans Inscription fournit de nets avantages par rapport aux techniques de déploiement traditionnelles.  Toutefois, certains avertissements et limitations doivent également être pris en compte.  La plus grande limitation est qu'il ne fonctionne que sous Windows XP ou supérieur.  L'implémentation de COM sans inscription a exigé des modifications quant au mode de chargement des composants dans le système d'exploitation principal.  Malheureusement, il n'existe aucune prise en charge descendante de COM sans inscription.  
  
 Tous les composants ne sont pas appropriés pour COM sans inscription.  Un composant n'est pas approprié si l'une des conditions suivantes est satisfaite :  
  
-   Le composant est un serveur out\-of\-process.  Les serveurs EXE ne sont pas pris en charge ; seules les DLL le sont.  
  
-   Le composant fait partie du système d'exploitation ou est un composant système, tel que XML, Internet Explorer ou MDAC \(Microsoft Data Access Components\).  Vous devez respecter la stratégie de redistribution de l'auteur du composant ; contactez votre fournisseur.  
  
-   Le composant fait partie d'une application, telle que Microsoft Office.  Par exemple, vous ne devez pas tenter d'isoler le modèle objet Microsoft Excel.  Il fait partie d'Office et ne peut être utilisé que sur un ordinateur sur lequel l'intégralité du produit Office est installée.  
  
-   Le composant est destiné à une utilisation comme complément ou comme composant logiciel enfichable, par exemple un complément Office ou un contrôle dans un navigateur Web.  Ce type de composant exige généralement une inscription définie par l'environnement d'hébergement, qui dépasse la portée du manifeste proprement dit.  
  
-   Le composant gère un périphérique physique ou virtuel pour le système, par exemple un pilote de périphérique pour un spouleur d'imprimante.  
  
-   Le composant est un redistribuable Data Access.  Pour pouvoir s'exécuter, les applications de données exigent généralement l'installation d'un redistribuable Data Access distinct.  Vous ne devez pas essayer d'isoler des composants tels que le contrôle de données Microsoft ADO, Microsoft OLE DB ou MDAC \(Microsoft Data Access Components\).  Si votre application utilise MDAC ou SQL Server Express, vous devez plutôt les définir comme composants requis ; consultez [How to: Install Prerequisites with a ClickOnce Application](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md).  
  
 Dans certains cas, il se peut que le développeur du composant puisse le reconcevoir pour COM sans inscription.  Si ce n'est pas possible, vous pouvez toujours générer et publier des applications qui en dépendent, par l'intermédiaire du modèle d'inscription standard à l'aide du programme d'amorçage.  Pour plus d'informations, consultez [Création de packages de programme d'amorçage](../deployment/creating-bootstrapper-packages.md).  
  
 Un composant COM ne peut être isolé qu'une fois par application.  Par exemple, vous ne pouvez pas isoler le même composant COM de deux projets **Bibliothèque de classes** différents qui font partie de la même application.  Cela entraînerait un avertissement de build, et le chargement de l'application échouerait au moment de l'exécution.  Pour éviter ce problème, Microsoft recommande d'encapsuler les composants COM dans une bibliothèque de classes unique.  
  
 Il existe plusieurs scénarios dans lesquels l'inscription COM est nécessaire sur l'ordinateur du développeur, même si le déploiement de l'application n'existe pas d'inscription.  La propriété `Isolated` exige l'inscription du composant COM sur l'ordinateur du développeur afin de générer automatiquement le manifeste pendant la création.  Aucune fonction capturant l'inscription n'appelle l'inscription automatique pendant la génération.  En outre, toute classe non définie explicitement dans la bibliothèque de types n'est pas reflétée dans le manifeste.  Lors de l'utilisation d'un composant COM avec un manifeste préexistant, tel qu'une référence native, il se peut que le composant ne doive pas être inscrit au moment du développement.  Toutefois, l'inscription est requise si le composant est un contrôle ActiveX et si vous souhaitez l'inclure dans la **boîte à outils** et dans le Concepteur Windows Forms.  
  
## Voir aussi  
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)