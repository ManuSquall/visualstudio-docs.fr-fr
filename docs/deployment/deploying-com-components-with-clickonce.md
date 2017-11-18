---
title: "Déploiement de composants COM avec ClickOnce | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: d3a8ae32afec789595ecd126eeaee0c5ea05a9e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="deploying-com-components-with-clickonce"></a>Déploiement de composants COM avec ClickOnce
Déploiement de composants COM hérités a toujours été une tâche difficile. Les composants doivent être inscrits globalement et peuvent donc entraîner des effets secondaires indésirables entre les applications qui se chevauche. Cette situation n’est généralement pas un problème dans les applications .NET Framework, car les composants sont complètement isolés de l’application ou sont compatibles avec le côte à côte. Visual Studio vous permet de déployer des composants COM isolés sur Windows XP ou système d’exploitation ultérieur.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]fournit un mécanisme simple et sécurisé pour le déploiement de vos applications .NET. Toutefois, si vos applications utilisent des composants COM hérités, vous devrez effectuer des étapes supplémentaires pour les déployer. Cette rubrique décrit comment déployer des composants COM isolés et référencer des composants natifs (par exemple, à partir de Visual Basic 6.0 ou Visual C++).  
  
 Pour plus d’informations sur le déploiement des composants COM isolés, consultez « Déploiement d’applications simplifié avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] et COM sans inscription « à [http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx](http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx).  
  
## <a name="registration-free-com"></a>COM sans inscription  
 COM sans inscription est une nouvelle technologie de déploiement et d’activation des composants COM isolés. Il fonctionne en plaçant bibliothèque de tous les composants de types et les informations d’inscription qui sont généralement installées dans le Registre du système dans un fichier XML appelé manifeste, stocké dans le même dossier que l’application.  
  
 Isoler un composant COM nécessite qu’il soit inscrit sur l’ordinateur du développeur, mais il n’a pas à être enregistré sur l’ordinateur de l’utilisateur final. Pour isoler un composant COM, il vous souhaitez de sa référence a la valeur **isolé** propriété **True**. Par défaut, cette propriété est définie **False**, indiquant qu’il doit être traité comme une référence COM inscrite. Si cette propriété est **True**, il génère un manifeste à générer pour ce composant au moment de la génération. Elle entraîne également les fichiers correspondants à copier dans le dossier de l’application lors de l’installation.  
  
 Lorsque le Générateur de manifeste rencontre une référence COM isolée, il énumère toutes les `CoClass` entrées dans la bibliothèque de types du composant, correspondant à chaque entrée aux données d’inscription correspondante et génération de définitions de manifeste pour tout le modèle COM classes dans le fichier de bibliothèque de types.  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>Déploiement des composants COM sans inscription à l’aide de ClickOnce  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]technologie de déploiement convient bien pour le déploiement de composants COM isolés, étant donné que les deux [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] et COM sans inscription requièrent qu’un composant ait un manifeste pour être déployé.  
  
 En règle générale, l’auteur du composant doit fournir un manifeste. Si ce n’est pas le cas, toutefois, Visual Studio est capable de générer automatiquement un manifeste pour un composant COM. La génération de manifeste s’effectue pendant la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] processus de publication ; pour plus d’informations, consultez [publication d’Applications ClickOnce](../deployment/publishing-clickonce-applications.md). Cette fonctionnalité vous permet également de tirer parti des composants hérités que vous avez créés dans des environnements de développement antérieurs tels que Visual Basic 6.0.  
  
 Il existe deux manières qui [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploie les composants COM :  
  
-   Utilisez le programme d’amorçage pour déployer vos composants COM ; Cela fonctionne sur toutes les plateformes prises en charge.  
  
-   Utilisez le composant natif d’isolement (également appelé COM sans inscription) déploiement. Toutefois, cela fonctionne uniquement sur un Windows XP ou un système d’exploitation ultérieur.  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Exemple d’isolation et de déploiement d’un composant COM Simple  
 Pour illustrer le déploiement du composant COM sans inscription, cet exemple montre comment créer une application Windows en Visual Basic qui fait référence à un composant COM natif isolé créé à l’aide de Visual Basic 6.0 et le déployer à l’aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Vous devez tout d’abord créer le composant COM natif :  
  
##### <a name="to-create-a-native-com-component"></a>Pour créer un composant COM natif  
  
1.  À l’aide de Visual Basic 6.0, à partir de la **fichier** menu, cliquez sur **nouveau**, puis **projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, sélectionnez le **Visual Basic** nœud et sélectionnez un **DLL ActiveX** projet. Dans la zone **Nom**, tapez `VB6Hello`.  
  
    > [!NOTE]
    >  Types de projets DLL ActiveX et contrôle ActiveX sont pris en charge avec COM sans inscription ; Types de projets EXE ActiveX et ActiveX Document ne sont pas pris en charge.  
  
3.  Dans **l’Explorateur de solutions**, double-cliquez sur **Class1.vb** pour ouvrir l’éditeur de texte.  
  
4.  Dans Class1.vb, ajoutez le code suivant après le code généré pour le `New` méthode :  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  Générez le composant. À partir de la **générer** menu, cliquez sur **générer la Solution**.  
  
> [!NOTE]
>  COM sans inscription prend en charge uniquement les DLL et COM contrôle les types de projet. Vous ne pouvez pas utiliser les fichiers exe avec COM sans inscription.  
  
 Vous pouvez maintenant créer une application Windows et ajoutez une référence au composant COM à elle.  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>Pour créer une application Windows à l’aide d’un composant COM  
  
1.  À l’aide de Visual Basic, à partir de la **fichier** menu, cliquez sur **nouveau**, puis **projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, sélectionnez le **Visual Basic** nœud et sélectionnez **Application Windows**. Dans la zone **Nom**, tapez `RegFreeComDemo`.  
  
3.  Dans **l’Explorateur de solutions**, cliquez sur le **afficher tous les fichiers** bouton pour afficher les références de projet.  
  
4.  Cliquez sur le **références** nœud et sélectionnez **ajouter une référence** dans le menu contextuel.  
  
5.  Dans le **ajouter une référence** boîte de dialogue, cliquez sur le **Parcourir** onglet, naviguez jusqu’au fichier VB6Hello.dll, puis sélectionnez-le.  
  
     A **VB6Hello** référence s’affiche dans la liste des références.  
  
6.  Pointez sur le **boîte à outils**, sélectionnez un **bouton** contrôler et faites-la glisser vers le **Form1** formulaire.  
  
7.  Dans le **propriétés** fenêtre, affectez à la **texte** propriété **Hello**.  
  
8.  Double-cliquez sur le bouton pour ajouter le code du gestionnaire et dans le fichier de code, ajoutez le code afin que le gestionnaire se présente comme suit :  
  
    ```  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
        Dim VbObj As New VB6Hello.Class1  
        VbObj.SayHello()  
    End Sub  
    ```  
  
9. Exécutez l'application. À partir de la **déboguer** menu, cliquez sur **démarrer le débogage**.  
  
 Ensuite, vous devez isoler le contrôle. Chaque composant COM que votre application utilise est représenté dans votre projet comme une référence COM. Ces références sont visibles sous le **références** nœud dans le **l’Explorateur de solutions** fenêtre. (Notez que vous pouvez ajouter des références directement à l’aide du **ajouter une référence** commande sur le **projet** menu, ou indirectement en faisant glisser un contrôle ActiveX sur votre formulaire.)  
  
 Les étapes suivantes montrent comment isoler le composant COM et de publier l’application de mises à jour qui contient le contrôle isolé :  
  
##### <a name="to-isolate-a-com-component"></a>Pour isoler un composant COM  
  
1.  Dans **l’Explorateur de solutions**, dans le **références** nœud, sélectionnez le **VB6Hello** référence.  
  
2.  Dans le **propriétés** fenêtre, modifiez la valeur de la **isolé** propriété à partir de **False** à **True**.  
  
3.  À partir de la **générer** menu, cliquez sur **générer la Solution**.  
  
 Désormais, lorsque vous appuyez sur F5, l’application fonctionne comme prévu, mais il est en cours d’exécution sous COM sans inscription. Afin de prouver, essayez d’annuler l’inscription du composant VB6Hello.dll et d’exécuter RegFreeComDemo1.exe en dehors de l’IDE de Visual Studio. Cette fois, lorsque le bouton est activé, il fonctionne toujours. Si vous renommez temporairement le manifeste d’application, il échouera à nouveau.  
  
> [!NOTE]
>  Vous pouvez simuler l’absence d’un composant COM en annulant temporairement son enregistrement. Ouvrez une invite de commandes, accédez à votre dossier système en tapant `cd /d %windir%\system32`, puis annulez l’inscription du composant en tapant `regsvr32 /u VB6Hello.dll`. Vous pouvez l’inscrire à nouveau en tapant `regsvr32 VB6Hello.dll`.  
  
 L’étape finale consiste à publier l’application à l’aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Pour publier une mise à jour de l’application avec un composant COM isolé  
  
1.  À partir de la **générer** menu, cliquez sur **Publier RegFreeComDemo**.  
  
     L'Assistant Publication apparaît.  
  
2.  Dans l’Assistant Publication, spécifiez un emplacement sur le disque de l’ordinateur local où vous pouvez accéder et examinez les fichiers publiés.  
  
3.  Cliquez sur **Terminer** pour publier l’application.  
  
 Si vous examinez les fichiers publiés, vous noterez que le fichier sysmon.ocx est inclus. Le contrôle est totalement isolé de cette application, c'est-à-dire que si l’ordinateur de l’utilisateur final possède une autre application à l’aide d’une version différente du contrôle, il ne peut pas interférer avec cette application.  
  
## <a name="referencing-native-assemblies"></a>Référencer des assemblys natifs  
 Visual Studio prend en charge les références à Visual Basic 6.0 ou natifs assemblys C++ ; Ces références sont appelées des références natives. Vous pouvez indiquer si une référence est native en vérifiant que son **Type de fichier** est définie sur **natif** ou **ActiveX**.  
  
 Pour ajouter une référence native, utilisez la **ajouter une référence** de commandes, puis naviguez jusqu’au manifeste. Certains composants placent le manifeste à l’intérieur de la DLL. Dans ce cas, vous pouvez simplement choisir la DLL proprement dite et Visual Studio ajoutera comme une référence native s’il détecte que le composant contient un manifeste incorporé. Visual Studio inclut également automatiquement les fichiers dépendants ou les assemblys répertoriés dans le manifeste s’ils sont dans le même dossier que le composant référencé.  
  
 Isolation d’un contrôle COM rend facile à déployer des composants COM qui n’ont pas déjà les manifestes. Toutefois, si un composant est fourni avec un manifeste, vous pouvez référencer directement le manifeste. En fait, vous devez toujours utiliser le manifeste fourni par l’auteur du composant dans la mesure du possible, au lieu d’utiliser le **isolé** propriété.  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>Limitations du déploiement d’un composant COM sans inscription  
 COM sans inscription fournit des avantages sur les techniques de déploiement traditionnelles. Toutefois, il existe quelques limitations et les avertissements qui doivent être précisés. La plus grande limitation est qu’il fonctionne uniquement sur Windows XP ou version ultérieure. L’implémentation de COM sans inscription ont imposé des changements à celui dans lequel les composants sont chargés dans le système d’exploitation principal. Malheureusement, il n’existe aucune couche de prise en charge de bas niveau pour COM sans inscription.  
  
 Pas de chaque composant est un candidat approprié pour COM sans inscription. Un composant n’est pas approprié si une des conditions suivantes est vraie :  
  
-   Le composant est un serveur out-of-process. Les serveurs EXE ne sont pas pris en charge ; Seules les DLL sont pris en charge.  
  
-   Le composant fait partie du système d’exploitation, ou est un composant du système, telles que XML, Internet Explorer ou Microsoft Data Access Components (MDAC). Vous devez suivre la stratégie de redistribution de l’auteur du composant ; Vérifiez auprès du fournisseur.  
  
-   Le composant fait partie d’une application, telles que Microsoft Office. Par exemple, vous ne devez pas tenter d’isoler le modèle objet de Microsoft Excel. Cela fait partie de Microsoft Office et peut uniquement être utilisé sur un ordinateur avec le produit Office intégral installé.  
  
-   Le composant est destiné à utiliser comme un complément ou d’un composant logiciel enfichable, par exemple un complément Office dans un contrôle ou dans un navigateur Web. Ces composants requièrent généralement une sorte de modèle d’inscription définie par l’environnement d’hébergement qui dépasse le cadre du manifeste lui-même.  
  
-   Le composant gère un périphérique physique ou virtuel pour le système, par exemple, un pilote de périphérique pour un spouleur d’impression.  
  
-   Le composant est un redistribuable Data Access. Les applications de données requièrent généralement un redistribuable Data Access distinct être installé avant de pouvoir exécuter. Vous ne devez pas essayer d’isoler des composants tels que le contrôle de données Microsoft ADO, OLE DB de Microsoft ou Microsoft Data Access Components (MDAC). Au lieu de cela, si votre application utilise MDAC ou SQL Server Express, vous devez les définir comme composants requis ; consultez [Comment : installer les composants requis avec une Application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
 Dans certains cas, il peut être possible pour le développeur du composant puisse le reconcevoir pour COM sans inscription. Si ce n’est pas possible, vous pouvez toujours générer et publier des applications qui dépendent d’elles par le biais du modèle d’inscription standard à l’aide du programme d’amorçage. Pour plus d’informations, consultez [création de Packages de programme d’amorçage](../deployment/creating-bootstrapper-packages.md).  
  
 Un composant COM ne peut être isolé qu’une seule fois par application. Par exemple, vous ne pouvez pas isoler le même composant COM à partir de deux **bibliothèque de classes** projets qui font partie de la même application. Cela entraînerait un avertissement de génération et l’application ne sera pas chargé au moment de l’exécution. Pour éviter ce problème, Microsoft recommande d’encapsuler des composants COM dans une bibliothèque de classes unique.  
  
 Il existe plusieurs scénarios dans quel COM, l’inscription est requise sur l’ordinateur du développeur, même si le déploiement de l’application ne nécessite pas d’enregistrement. Le `Isolated` propriété requiert que l’inscription du composant COM sur l’ordinateur du développeur afin de générer automatiquement le manifeste pendant la génération. Il n’existe aucune fonctionnalité de capture de l’enregistrement qui appellent l’inscription automatique pendant la génération. En outre, toutes les classes ne sont pas explicitement définis dans la bibliothèque de types seront répercutées dans le manifeste. Lors de l’utilisation d’un composant COM avec un manifeste existant, par exemple une référence native, le composant ne peut pas besoin être inscrit au moment du développement. Toutefois, l’inscription est requise si le composant est un contrôle ActiveX et que vous souhaitez inclure dans le **boîte à outils** et le Concepteur Windows Forms.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)