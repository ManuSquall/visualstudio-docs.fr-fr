---
title: Déploiement de composants COM avec ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7032ec5ae03febf6c54978020379769ac742a136
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839677"
---
# <a name="deploy-com-components-with-clickonce"></a>Déployer des composants COM avec ClickOnce
Le déploiement de composants COM hérités a traditionnellement été une tâche difficile. Les composants doivent être inscrits globalement, ce qui peut entraîner des effets secondaires indésirables entre les applications qui se chevauchent. Cette situation n’est généralement pas un problème dans les applications .NET Framework, car les composants sont complètement isolés dans une application ou sont compatibles côte à côte. Visual Studio vous permet de déployer des composants COM isolés sur le système d’exploitation Windows XP ou version ultérieure.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fournit un mécanisme simple et sécurisé pour le déploiement de vos applications .NET. Toutefois, si vos applications utilisent des composants COM hérités, vous devrez prendre des mesures supplémentaires pour les déployer. Cette rubrique décrit comment déployer des composants COM isolés et référencer des composants natifs (par exemple, à partir de Visual Basic 6,0 ou Visual C++).

 Pour plus d’informations sur le déploiement de composants COM isolés, consultez [simplifier le déploiement d’applications avec ClickOnce et com sans inscription](https://web.archive.org/web/20050326005413/msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx).

## <a name="registration-free-com"></a>COM sans inscription
 Le modèle COM sans inscription est une nouvelle technologie pour le déploiement et l’activation de composants COM isolés. Il fonctionne en plaçant toutes les informations de bibliothèque de types et d’inscription du composant qui sont généralement installées dans le registre système dans un fichier XML appelé manifeste, stocké dans le même dossier que l’application.

 L’isolation d’un composant COM requiert qu’il soit inscrit sur l’ordinateur du développeur, mais qu’il n’a pas besoin d’être inscrit sur l’ordinateur de l’utilisateur final. Pour isoler un composant COM, il vous suffit de définir la propriété **isolated** de sa référence sur **true**. Par défaut, cette propriété a la valeur **false**, ce qui indique qu’elle doit être traitée comme une référence com inscrite. Si cette propriété a la **valeur true**, elle provoque la génération d’un manifeste pour ce composant au moment de la génération. Cela entraîne également la copie des fichiers correspondants dans le dossier de l’application lors de l’installation.

 Lorsque le générateur de manifeste rencontre une référence COM isolée, il énumère toutes les `CoClass` entrées dans la bibliothèque de types du composant, en faisant correspondre chaque entrée avec ses données d’inscription correspondantes et en générant des définitions de manifeste pour toutes les classes com dans le fichier bibliothèque de types.

## <a name="deploy-registration-free-com-components-using-clickonce"></a>Déployez des composants COM sans inscription à l’aide de ClickOnce
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la technologie de déploiement est bien adaptée au déploiement de composants COM isolés, car [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] et com sans inscription requièrent qu’un composant ait un manifeste pour être déployé.

 En règle générale, l’auteur du composant doit fournir un manifeste. Si ce n’est pas le cas, Visual Studio peut générer automatiquement un manifeste pour un composant COM. La génération du manifeste est effectuée pendant le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] processus de publication. pour plus d’informations, consultez [publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md). Cette fonctionnalité vous permet également de tirer parti des composants hérités que vous avez créés dans des environnements de développement antérieurs, par exemple Visual Basic 6,0.

 Il existe deux façons de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déployer des composants com :

- Utilisez le programme d’amorçage pour déployer vos composants COM ; Cela fonctionne sur toutes les plateformes prises en charge.

- Utilisez le déploiement de l’isolation de composant natif (également appelé COM sans inscription). Toutefois, cela ne fonctionne que sur un système d’exploitation Windows XP ou version ultérieure.

### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Exemple d’isolation et de déploiement d’un composant COM simple
 Pour illustrer le déploiement de composants COM sans inscription, cet exemple crée une application Windows dans Visual Basic qui référence un composant COM natif isolé créé à l’aide de Visual Basic 6,0 et le déploie à l’aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

 Tout d’abord, vous devez créer le composant COM natif :

##### <a name="to-create-a-native-com-component"></a>Pour créer un composant COM natif

1. À l’aide de Visual Basic 6,0, dans le menu **fichier** , cliquez sur **nouveau**, puis sur **projet**.

2. Dans la boîte de dialogue **nouveau projet** , sélectionnez le nœud **Visual Basic** et sélectionnez un projet **DLL ActiveX** . Dans le champ **Nom**, saisissez `VB6Hello`.

    > [!NOTE]
    > Seuls les types de projets DLL ActiveX et contrôle ActiveX sont pris en charge avec COM sans inscription ; Les types de projets EXE ActiveX et document ActiveX ne sont pas pris en charge.

3. Dans **Explorateur de solutions**, double-cliquez sur **Class1. vb** pour ouvrir l’éditeur de texte.

4. Dans Class1. vb, ajoutez le code suivant après le code généré pour la `New` méthode :

    ```vb
    Public Sub SayHello()
       MsgBox "Message from the VB6Hello COM component"
    End Sub
    ```

5. Générez le composant. Dans le menu **Générer**, cliquez sur **Générer la solution**.

> [!NOTE]
> COM sans inscription prend en charge uniquement les types de projets dll et contrôles COM. Vous ne pouvez pas utiliser les fichiers exe avec COM sans inscription.

 Vous pouvez maintenant créer une application Windows et y ajouter une référence au composant COM.

##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>Pour créer une application basée sur Windows à l’aide d’un composant COM

1. À l’aide de Visual Basic, dans le menu **fichier** , cliquez sur **nouveau**, puis sur **projet**.

2. Dans la boîte de dialogue **nouveau projet** , sélectionnez le nœud **Visual Basic** , puis sélectionnez **application Windows**. Dans le champ **Nom**, saisissez `RegFreeComDemo`.

3. Dans **Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers** pour afficher les références de projet.

4. Cliquez avec le bouton droit sur le nœud **références** et sélectionnez **Ajouter une référence** dans le menu contextuel.

5. Dans la boîte de dialogue **Ajouter une référence** , cliquez sur l’onglet **Parcourir** , accédez à VB6Hello.dll, puis sélectionnez-le.

    Une référence **VB6Hello** s’affiche dans la liste Références.

6. Pointez sur la **boîte à outils**, sélectionnez un contrôle **Button** , puis faites-le glisser vers le formulaire **Form1** .

7. Dans la fenêtre **Propriétés** , affectez à la propriété **Text** du bouton la valeur **Hello**.

8. Double-cliquez sur le bouton pour ajouter le code du gestionnaire, puis, dans le fichier de code, ajoutez le code afin que le gestionnaire lise les éléments suivants :

   ```vb
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
       Dim VbObj As New VB6Hello.Class1
       VbObj.SayHello()
   End Sub
   ```

9. Exécutez l'application. Dans le menu **Déboguer**, cliquez sur **Démarrer le débogage**.

   Vous devez ensuite isoler le contrôle. Chaque composant COM utilisé par votre application est représenté dans votre projet sous la forme d’une référence COM. Ces références sont visibles sous le nœud **références** dans la fenêtre **Explorateur de solutions** . (Notez que vous pouvez ajouter des références directement à l’aide de la commande **Ajouter une référence** dans le menu **projet** , ou indirectement en faisant glisser un contrôle ActiveX sur votre formulaire.)

   Les étapes suivantes montrent comment isoler le composant COM et publier l’application mise à jour contenant le contrôle isolé :

##### <a name="to-isolate-a-com-component"></a>Pour isoler un composant COM

1. Dans **Explorateur de solutions**, dans le nœud **références** , sélectionnez la référence **VB6Hello** .

2. Dans la fenêtre **Propriétés** , remplacez la valeur **false** de la propriété **isolated** par **true**.

3. Dans le menu **Générer**, cliquez sur **Générer la solution**.

   Désormais, lorsque vous appuyez sur F5, l’application fonctionne comme prévu, mais elle s’exécute maintenant sous COM sans inscription. Pour prouver cela, essayez d’annuler l’inscription du composant VB6Hello.dll et d’exécuter RegFreeComDemo1.exe en dehors de l’IDE de Visual Studio. Cette fois, lorsque vous cliquez sur le bouton, il fonctionne toujours. Si vous renommez temporairement le manifeste de l’application, il échouera à nouveau.

> [!NOTE]
> Vous pouvez simuler l’absence d’un composant COM en le désinscrivant temporairement. Ouvrez une invite de commandes, accédez à votre dossier système en tapant `cd /d %windir%\system32` , puis annulez l’inscription du composant en tapant `regsvr32 /u VB6Hello.dll` . Vous pouvez l’inscrire à nouveau en tapant `regsvr32 VB6Hello.dll` .

 La dernière étape consiste à publier l’application à l’aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] :

##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Pour publier une mise à jour d’application avec un composant COM isolé

1. Dans le menu **générer** , cliquez sur **Publier RegFreeComDemo**.

    L'Assistant Publication apparaît.

2. Dans l’Assistant publication, spécifiez un emplacement sur le disque de l’ordinateur local où vous pouvez accéder aux fichiers publiés et les examiner.

3. Cliquez sur **Terminer** pour publier l’application.

   Si vous examinez les fichiers publiés, vous remarquerez que le fichier sysmon. ocx est inclus. Le contrôle est totalement isolé dans cette application, ce qui signifie que si l’ordinateur de l’utilisateur final a une autre application utilisant une version différente du contrôle, il ne peut pas interférer avec cette application.

## <a name="reference-native-assemblies"></a>Assemblys natifs de référence
 Visual Studio prend en charge les références aux assemblys natifs Visual Basic 6,0 ou C++; ces références sont appelées références natives. Vous pouvez savoir si une référence est native en vérifiant que sa propriété **type de fichier** est définie sur **natif** ou **ActiveX**.

 Pour ajouter une référence native, utilisez la commande **Ajouter une référence** , puis accédez au manifeste. Certains composants placent le manifeste à l’intérieur de la DLL. Dans ce cas, vous pouvez simplement choisir la DLL elle-même et Visual Studio l’ajoute en tant que référence Native si elle détecte que le composant contient un manifeste incorporé. Visual Studio inclut également automatiquement tous les fichiers ou assemblys dépendants répertoriés dans le manifeste s’ils se trouvent dans le même dossier que le composant référencé.

 L’isolation des contrôles COM facilite le déploiement des composants COM qui n’ont pas encore de manifestes. Toutefois, si un composant est fourni avec un manifeste, vous pouvez référencer directement le manifeste. En fait, vous devez toujours utiliser le manifeste fourni par l’auteur du composant, dans la mesure du possible, plutôt que d’utiliser la propriété **isolated** .

## <a name="limitations-of-registration-free-com-component-deployment"></a>Limitations du déploiement de composants COM sans inscription
 COM sans inscription offre des avantages clairs par rapport aux techniques de déploiement traditionnelles. Toutefois, il existe quelques limitations et avertissements qui doivent également être signalés. La plus grande limitation est qu’elle fonctionne uniquement sur Windows XP ou version ultérieure. L’implémentation de COM sans inscription nécessitait des modifications de la façon dont les composants sont chargés dans le système d’exploitation principal. Malheureusement, il n’existe aucune couche de prise en charge de niveau inférieure pour COM sans inscription.

 Tous les composants ne sont pas un candidat approprié pour COM sans inscription. Un composant n’est pas approprié si l’une des conditions suivantes est vraie :

- Le composant est un serveur hors processus. Les serveurs EXE ne sont pas pris en charge ; seules les dll sont prises en charge.

- Le composant fait partie du système d’exploitation ou est un composant système, tel que XML, Internet Explorer ou MDAC (Microsoft Data Access Components). Vous devez suivre la stratégie de redistribution de l’auteur du composant ; Vérifiez auprès de votre fournisseur.

- Le composant fait partie d’une application, par exemple Microsoft Office. Par exemple, vous ne devez pas essayer d’isoler le modèle objet Microsoft Excel. Ce composant fait partie d’Office et ne peut être utilisé que sur un ordinateur sur lequel est installé le produit Office complet.

- Le composant est destiné à être utilisé comme complément ou comme composant logiciel enfichable, par exemple un complément Office ou un contrôle dans un navigateur Web. De tels composants nécessitent généralement un type de schéma d’inscription défini par l’environnement d’hébergement qui est au-delà de la portée du manifeste lui-même.

- Le composant gère un appareil physique ou virtuel pour le système, par exemple, un pilote de périphérique pour un spouleur d’impression.

- Le composant est un redistribuable d’accès aux données. En général, les applications de données nécessitent l’installation d’un package redistribuable d’accès aux données distinct pour pouvoir s’exécuter. Vous ne devez pas essayer d’isoler des composants tels que le contrôle de données Microsoft ADO, Microsoft OLE DB ou MDAC (Microsoft Data Access Components). Au lieu de cela, si votre application utilise MDAC ou SQL Server Express, vous devez les définir comme conditions préalables. consultez [Comment : installer les composants requis avec une application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).

  Dans certains cas, il est possible pour le développeur du composant de le reconcevoir pour COM sans inscription. Si ce n’est pas possible, vous pouvez toujours générer et publier des applications qui en dépendent par le biais du schéma d’inscription standard à l’aide du programme d’amorçage. Pour plus d’informations, consultez [création de packages de programme d’amorçage](../deployment/creating-bootstrapper-packages.md).

  Un composant COM ne peut être isolé qu’une seule fois par application. Par exemple, vous ne pouvez pas isoler le même composant COM de deux projets de **bibliothèque de classes** différents qui font partie de la même application. Cela génère un avertissement de génération et l’application ne se charge pas au moment de l’exécution. Afin d’éviter ce problème, Microsoft vous recommande d’encapsuler les composants COM dans une bibliothèque de classes unique.

  Il existe plusieurs scénarios dans lesquels l’inscription COM est requise sur l’ordinateur du développeur, même si le déploiement de l’application ne nécessite pas d’inscription. La `Isolated` propriété requiert l’inscription du composant com sur l’ordinateur du développeur afin de générer automatiquement le manifeste pendant la génération. Il n’existe aucune fonctionnalité de capture d’inscription qui appelle l’inscription automatique pendant la génération. En outre, toutes les classes qui ne sont pas explicitement définies dans la bibliothèque de types ne seront pas reflétées dans le manifeste. Lors de l’utilisation d’un composant COM avec un manifeste préexistant, tel qu’une référence native, il se peut que le composant n’ait pas besoin d’être inscrit au moment du développement. Toutefois, l’inscription est requise si le composant est un contrôle ActiveX et que vous souhaitez l’inclure dans la **boîte à outils** et dans le concepteur de Windows Forms.

## <a name="see-also"></a>Voir aussi
- [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)