---
title: Résoudre les erreurs dans les solutions Office
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.DesignerDisabled
- VST.Designer.CannotActivate
- VST.Project.ExcelBusy
- VST.SelectDocWizard.AlreadyCustomized
- VST.SelectDocWizard.DocPath
- VST.Project.CannotOpen
- VST.Designer.ErrorsOccurred
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2aa971a79c0b0f5592c0da5c52a457c585bb0f15
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985573"
---
# <a name="troubleshoot-errors-in-office-solutions"></a>Résoudre les erreurs dans les solutions Office
  Vous pouvez rencontrer des problèmes quand vous effectuez les tâches suivantes en développant des solutions Office dans Visual Studio :

- [Créer, mettre à niveau et ouvrir des projets](#creating)

- [Utiliser les concepteurs](#designers)

- [Écrire du code](#code)

- [Générer des projets](#building)

- [Déboguer des projets](#debugging)

## <a name="creating"></a>Créer, mettre à niveau et ouvrir des projets
 Vous pouvez rencontrer les erreurs suivantes quand vous créez ou ouvrez des projets Office.

### <a name="the-project-cannot-be-created"></a>Impossible de créer le projet
 Une erreur s'est produite quand vous avez essayé de créer ou d'ouvrir un projet Office, mais Visual Studio ne disposait pas de suffisamment d'informations pour en déterminer la cause. Essayez de fermer votre projet, de quitter Visual Studio et de le démarrer de nouveau.

 Si vous essayez de créer un projet au niveau du document, il est possible qu'un autre document du même nom que le document dans le nouveau projet soit déjà ouvert dans Excel ou Word. Assurez-vous que toutes les autres instances d'Excel ou de Word soient fermées.

### <a name="control-properties-are-lost-when-you-create-a-new-project-based-on-a-document-from-an-existing-project"></a>Les propriétés du contrôle sont perdues quand vous créez un projet basé sur un document à partir d’un projet existant
 Si vous créez un nouveau projet Office basé sur un document issu d'un projet existant, aucune propriété des contrôles qui se trouvent sur le document n'est copiée dans le nouveau projet. Vous devez réinitialiser manuellement les propriétés de tous les contrôles préexistants. Vous pouvez également conserver les propriétés des contrôles en créant une copie du projet existant au lieu de créer un nouveau projet, ou en chargeant le projet existant dans la nouvelle solution (dans le concepteur) et en effectuant un copier-coller des contrôles du document existant dans le nouveau document.

### <a name="errors-when-you-create-an-excel-workbook-project-based-on-an-existing-workbook"></a>Erreurs lors de la création d’un projet de classeur Excel basé sur un classeur existant
 Si vous créez un projet de classeur Excel basé sur un classeur existant, vous pouvez voir une combinaison des erreurs suivantes.

 Dans Excel : « Avertissement concernant la confidentialité : ce document contient des macros, des contrôles ActiveX, des informations sur le kit d'extension XML ou des composants Web. Ils peuvent renfermer des informations personnelles qui ne peuvent pas être supprimées par l'Inspecteur de document. »

 Dans Visual Studio : « Le chargement du concepteur n'a pas pu s'effectuer correctement. »

 Ces erreurs peuvent se produire si vous essayez de créer un projet basé sur un classeur dont les informations personnelles ont été supprimées à l'aide de l'inspecteur de document. Pour éviter cette erreur, effectuez les opérations suivantes avant de créer le projet.

1. Ouvrez le classeur dans Excel.

2. Dans Excel, ouvrez le Centre de gestion de la confidentialité.

3. Dans l’onglet **options de confidentialité** , désactivez la case à cocher Supprimer les **informations personnelles des propriétés du fichier lors de l’enregistrement** .

4. Enregistrez le classeur et fermez Excel.

### <a name="cannot-open-a-project-after-migration"></a>Impossible d’ouvrir un projet après la migration
 Après la migration d'une solution Office vers Microsoft Office 2010, le projet ne peut pas être ouvert sur un ordinateur de développement doté uniquement de la version 2007 de Microsoft Office System. Vous pouvez voir les erreurs suivantes.

 « Un ou plusieurs projets de la solution n'ont pas été correctement chargés. Pour plus d'informations, consultez la fenêtre de Sortie. »

 « Impossible de créer le projet car l'application associée à ce type de projet n'est pas installée sur cet ordinateur. Vous devez installer l'application Microsoft Office associée à ce type de projet. »

 Pour résoudre ce problème, modifiez le fichier *. vbproj* ou *. csproj* . Pour un projet Word, remplacez HostPackage="{763FDC83-64E5-4651-AC9B-28C4FEB985A1}" par HostPackage="{6CE98B71-D55A-4305-87A8-0D6E368D9600}". Pour un projet Excel, remplacez HostPackage="{B284B16A-C42C-4438-BDCD-B72F4AC43CFB}" par HostPackage="{825100CF-0BA7-47EA-A084-DCF3308DAF74}". Pour un projet Outlook, remplacez HostPackage="{D2B20FF5-A6E5-47E1-90E8-463C6860CB05}" par HostPackage="{20A848B8-E01F-4801-962E-25DB0FF57389}".

 Vous pouvez également vous assurer que les projets migrés sont ouverts uniquement sur des ordinateurs de développement où Microsoft Office 2010 est déjà installé.

### <a name="errors-in-upgraded-office-2003-document-level-projects-that-contain-windows-forms-controls"></a>Erreurs dans les projets de niveau document Office 2003 mis à niveau qui contiennent des contrôles Windows Forms
 Si vous mettez à niveau un projet Microsoft Office 2003 au niveau du document et que le document contient des contrôles Windows Forms, le projet mis à niveau peut contenir des erreurs de compilation ou d’exécution. Pour éviter ce problème, installez Visual Studio 2005 Tools pour Office Second Edition Runtime sur l'ordinateur de développement avant de mettre à niveau le projet. Cette version du runtime est disponible sous forme de package redistribuable dans le Centre de téléchargement Microsoft : [Microsoft Visual Studio 2005 Tools pour Office Second Edition Runtime (VSTO 2005 SE) (x86)](https://www.microsoft.com/download/details.aspx?id=2392).

 Une fois la mise à niveau du projet terminée, vous pourrez désinstaller Visual Studio 2005 Tools pour Office Second Edition Runtime de l'ordinateur de développement s'il n'est pas utilisé par d'autres solutions Office.

## <a name="designers"></a>Utiliser les concepteurs
 Vous pouvez rencontrer les erreurs suivantes en utilisant le document, le classeur ou le concepteur de feuille de calcul dans des projets de niveau document.

### <a name="designer-failed-to-load-correctly"></a>Le concepteur n’a pas pu se charger correctement
 Visual Studio ne peut pas ouvrir le concepteur dans les cas suivants :

- Excel ou Word est déjà ouvert et affiche une boîte de dialogue modale. Pour ouvrir le concepteur, vérifiez si une boîte de dialogue Excel ou Word est ouverte, et fermez toute boîte de dialogue modale ouverte. Si aucune boîte de dialogue modale n'est ouverte, certaines actions supplémentaires peuvent être requises avant la réponse d'Excel ou de Word.

- Le projet est en cours de débogage. Pour ouvrir le concepteur, arrêtez ou terminez le débogage.

- Un complément Excel VSTO qui est installé sur l’ordinateur de développement affiche une boîte de dialogue au démarrage d’Excel. Pour créer un projet de niveau document Excel, vous devez tout d’abord désactiver le complément VSTO.

### <a name="controls-appear-as-black-rectangles-on-the-document-or-worksheet"></a>Les contrôles apparaissent sous forme de rectangles noirs sur le document ou la feuille de calcul
 Si vous groupez des contrôles dans un document ou une feuille de calcul, Visual Studio ne reconnaît plus les contrôles. Les contrôles groupés ne sont pas accessibles dans la fenêtre **Propriétés** et apparaissent sous forme de rectangles noirs sur le document ou la feuille de calcul. Vous devez dissocier les contrôles pour restaurer leurs fonctionnalités.

### <a name="controls-on-a-word-template-are-not-visible-in-visual-studio"></a>Les contrôles d’un modèle Word ne sont pas visibles dans Visual Studio
 Si vous ouvrez un modèle Word dans le concepteur Visual Studio, les contrôles du modèle qui ne sont pas alignés sur le texte peuvent ne pas être visibles. Cela est dû au fait que Visual Studio ouvre les modèles Word en mode **normal** . Pour afficher les contrôles, cliquez sur le menu **affichage** , pointez sur **Microsoft Office vue Word** , puis cliquez sur **page**.

### <a name="insert-clip-art-command-does-nothing-in-the-visual-studio-designer"></a>La commande INSERT clip art ne fait rien dans le concepteur Visual Studio
 Quand Excel ou Word est ouvert dans le concepteur Visual Studio, le fait de cliquer sur le bouton image **clipart** sous l’onglet **illustrations** du ruban n’ouvre pas le volet de tâches image **clipart** . Pour ajouter une image clipart, vous devez ouvrir la copie du classeur ou du document qui se trouve dans le dossier du projet principal (pas la copie qui se trouve dans le dossier *\Bin* ) en dehors de Visual Studio, ajouter l’image clipart, puis enregistrer le classeur ou le document.

## <a name="code"></a>Écrire du code
 Vous pouvez rencontrer les erreurs suivantes quand vous écrivez du code dans des projets Office.

### <a name="some-events-of-office-objects-are-not-accessible-when-using-c"></a>Certains événements des objets Office ne sont pas accessibles lors de l’utilisation de C\#
 Dans certains cas, une erreur du compilateur comme celle ci-dessous peut s'afficher quand vous essayez d'accéder à un événement particulier d'une instance d'un type d'assembly PIA (Primary Interop Assembly) Office dans un projet Visual C#.

 « Ambiguïté entre 'Microsoft.Office.Interop.Excel._Application.NewWorkbook' et 'Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook' »

 Cette erreur signifie que vous tentez d'accéder à un événement portant le même nom qu'une autre propriété ou méthode de l'objet. Pour accéder à l’événement, vous devez effectuer un cast de l’objet vers son *interface d’événement*.

 Les types d'assembly PIA Office possédant des événements implémentent deux interfaces : une interface principale contenant toutes les propriétés et méthodes ,et une interface d'événement contenant les événements exposés par l'objet. Ces interfaces d’événements utilisent la Convention d’affectation de noms *ObjectName*Events*n*_ event, par exemple <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> et <xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event>. Si vous ne pouvez pas accéder à un événement que vous vous attendez à trouver sur un objet, effectuez un cast de cet objet vers son interface d'événement.

 Par exemple, les objets <xref:Microsoft.Office.Interop.Excel.Application> possèdent un événement <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> et une propriété <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A>. Pour gérer l'événement <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook>, effectuez un cast de <xref:Microsoft.Office.Interop.Excel.Application> vers l'interface <xref:Microsoft.Office.Interop.Excel.AppEvents_Event>. L'exemple de code suivant montre comment procéder dans un projet au niveau du document pour Excel.

 [!code-csharp[Trin_VstcoreTroubleshootingExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingExcelCS/ThisWorkbook.cs#1)]

 Pour plus d’informations sur les interfaces d’événements dans les assemblys PIA Office, consultez [vue d’ensemble des classes et des interfaces dans les assemblys PIA (Primary Interop Assembly](/previous-versions/office/office-12//ms247299(v=office.12))) d’Office.

### <a name="cannot-reference-office-pia-classes-in-projects-that-target-the-includenet_v40_shortsharepointincludesnet-v40-short-mdmd-or-the-includenet_v45vstoincludesnet-v45-mdmd"></a>Impossible de référencer des classes d’assembly PIA Office dans des projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]
 Dans les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], le code qui fait référence à une classe définie dans un assembly PIA Office ne peut pas être compilé par défaut. Les classes dans les assemblys PIA utilisent la classe de convention d’affectation de noms *ObjectName*, par exemple <xref:Microsoft.Office.Interop.Word.DocumentClass> et <xref:Microsoft.Office.Interop.Excel.WorkbookClass>. Par exemple, le code suivant issu d’un projet de complément Word VSTO ne peut pas être compilé.

```vb
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;
```

 Ce code génère les erreurs de compilation suivantes :

- Visual Basic : "la référence à la classe’DocumentClass’n’est pas autorisée lorsque son assembly est lié en utilisant le mode no-PIA."

- Visuel C#: "Impossible d’incorporer le type Interop’Microsoft. Office. Interop. Word. DocumentClass'. Utilisez l'interface applicable à la place. »

  Pour résoudre cette erreur, modifiez le code pour faire référence à l'interface correspondante à la place. Par exemple, au lieu de faire référence à un objet <xref:Microsoft.Office.Interop.Word.DocumentClass>, faites référence à une instance de l'interface <xref:Microsoft.Office.Interop.Word.Document> à la place.

```vb
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;
```

 Les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] incorporent automatiquement tous les types d'interopérabilité des assemblys PIA Office par défaut. Cette erreur de compilation se produit parce que la fonctionnalité des types interop incorporés fonctionne uniquement avec les interfaces, et non pas avec les classes. Pour plus d’informations sur les interfaces et les classes des assemblys PIA Office, consultez [vue d’ensemble des classes et des interfaces dans les assemblys PIA (Primary Interop Assembly](/previous-versions/office/office-12/ms247299(v=office.12))) d’Office. Pour plus d’informations sur la fonctionnalité des types Interop incorporés dans les projets Office, consultez [conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md).

### <a name="references-to-office-classes-are-not-recognized"></a>Les références aux classes Office ne sont pas reconnues
 Certains noms de classes, par exemple application, se trouvent dans plusieurs espaces de noms tels que <xref:Microsoft.Office.Interop.Word> et <xref:System.Windows.Forms>. Pour cette raison, l’instruction **Imports**/**using** en haut des modèles de projet comprend une constante qualifiante abrégée, par exemple :

 [!code-csharp[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#2)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#2)]

 Cette utilisation de l’instruction **Imports**/**using** exige que vous différenciiez les références aux classes Office avec le qualificateur Word ou Excel, par exemple :

 [!code-csharp[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#3)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#3)]

 Vous obtenez des erreurs si vous utilisez une déclaration non qualifiée. Par exemple :

 [!code-csharp[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#4)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#4)]

 Même si vous avez importé l’espace de noms Word ou Excel et que vous avez accès à toutes les classes qu’il contient, vous devez qualifier complètement tous les types avec Word ou Excel pour supprimer l’ambiguïté relative aux espaces de noms.

## <a name="building"></a> Générer des projets
 Vous pouvez rencontrer les erreurs suivantes quand vous générez des projets Office.

### <a name="cannot-build-a-document-level-project-that-is-based-on-a-document-with-restricted-permissions"></a>Impossible de générer un projet au niveau du document basé sur un document avec des autorisations restreintes
 Visual Studio ne peut pas générer de projets de niveau document si le document a des autorisations limitées. Si votre projet contient un document qui a des autorisations restreintes, le projet ne se compile pas et le message suivant s’affiche dans la fenêtre **liste d’erreurs** .

 « Impossible d'ajouter la personnalisation. »

 Si vous souhaitez inclure un document doté d'autorisations restreintes, utilisez un document non restreint pendant que vous développez et générez la solution. Ensuite, appliquez les autorisations restreintes au document dans l'emplacement de publication, une fois la solution publiée.

### <a name="compiler-errors-occur-after-a-namedrange-control-is-deleted"></a>Des erreurs de compilateur se produisent après la suppression d’un contrôle NamedRange
 Si vous supprimez un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> d'une feuille de calcul qui n'est pas la feuille de calcul active dans le concepteur, il est possible que le code généré automatiquement ne soit pas supprimé de votre projet et que des erreurs du compilateur se produisent. Pour vous assurer que le code est supprimé, vous devez toujours sélectionner la feuille de calcul qui contient le contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> pour qu'elle devienne la feuille de calcul active avant la suppression du contrôle. Si le code généré automatiquement n'est pas supprimé quand vous supprimez le contrôle, vous pouvez entraîner la suppression du code par le concepteur en activant la feuille de calcul et en apportant une modification afin que la feuille de calcul soit marquée comme modifiée. Quand vous recréez le projet, le code est supprimé.

## <a name="debugging"></a>Déboguer des projets
 Vous pouvez rencontrer les erreurs suivantes quand vous déboguez des projets Office.

### <a name="prompt-to-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>L’invite de désinstallation s’affiche lorsque vous publiez et installez une solution sur l’ordinateur de développement
 Quand vous déboguez une solution Office, l'erreur suivante peut s'afficher.

 « La personnalisation ne peut pas être installée car une autre version est actuellement installée et ne peut pas être mise à niveau depuis cet emplacement. »

 Cette erreur indique que vous avez précédemment publié et installé la solution Office sur votre ordinateur de développement. Pour empêcher l'affichage de ce message, désinstallez la solution dans la liste des programmes installés sur l'ordinateur avant de déboguer la solution. Vous pouvez également créer un autre compte d'utilisateur sur votre ordinateur de développement pour tester l'installation de la solution publiée.

### <a name="document-level-projects-created-at-unc-network-locations-do-not-run-from-visual-studio"></a>Les projets au niveau du document créés aux emplacements réseau UNC ne s’exécutent pas à partir de Visual Studio
 Si vous créez un projet au niveau du document pour Excel ou Word dans un emplacement réseau UNC, vous devez ajouter l'emplacement du document à la liste des emplacements approuvés dans Excel ou Word. Sinon, la personnalisation n'est pas chargée quand vous essayez d'exécuter ou de déboguer le projet dans Visual Studio. Pour plus d’informations sur les emplacements approuvés, consultez accorder un niveau [de confiance à des documents](../vsto/granting-trust-to-documents.md).

### <a name="threads-are-not-stopped-correctly-after-debugging"></a>Les threads ne sont pas arrêtés correctement après le débogage
 Les projets Office dans Visual Studio suivent une convention d'affectation de noms de threads qui permet au débogueur de fermer le programme correctement. Si vous créez des threads dans votre solution, vous devez nommer chaque thread avec le préfixe VSTA_ afin de garantir que ces threads sont gérés correctement quand vous arrêtez le débogage. Par exemple, vous pouvez définir la propriété `Name` d’un thread qui attend un événement réseau sur **VSTA_NetworkListener**.

### <a name="cannot-run-or-debug-any-office-solution-on-the-development-computer"></a>Impossible d’exécuter ou de déboguer une solution Office sur l’ordinateur de développement
 Si vous ne pouvez pas exécuter ni développer un projet Office sur votre ordinateur de développement, le message d'erreur suivant peut s'afficher :

 « La personnalisation n'a pas pu être chargée, car le domaine d'application n'a pas pu être créé. »

 Visual Studio utilise Fusion, le chargeur d'assembly du .NET Framework, pour mettre en cache les assemblys avant de charger les solutions Office. Assurez-vous que Visual Studio peut écrire dans le cache de Fusion et réessayez. Pour plus d’informations, consultez [assemblys de clichés instantanés](/dotnet/framework/app-domains/shadow-copy-assemblies).

### <a name="error-when-stopping-the-debugger-in-a-document-level-project-after-using-edit-and-continue"></a>Erreur lors de l’arrêt du débogueur dans un projet au niveau du document après l’utilisation de modifier & continuer
 Si vous utilisez **modifier** & **Continuer** pour apporter des modifications au code dans un projet au niveau du document pour Excel ou Word alors que le projet est en mode arrêt, vous pouvez voir une boîte de dialogue avec le message d’erreur suivant si vous arrêtez par la suite le débogueur.

 « Si vous terminez le processus dans son état actuel, cela risque de produire des résultats indésirables notamment la perte de données et l'instabilité du système. »

 Que vous cliquiez sur **Oui** ou **non** dans la boîte de dialogue, Visual Studio met fin au processus Excel ou Word et arrête le débogueur. Pour arrêter le débogage du projet sans afficher cette boîte de dialogue, quittez Excel ou Word directement au lieu d'arrêter le débogueur dans Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Résoudre les problèmes des solutions Office](../vsto/troubleshooting-office-solutions.md)
- [Résoudre les problèmes de sécurité des solutions Office](../vsto/troubleshooting-office-solution-security.md)
- [Résoudre les problèmes de déploiement de solutions Office](../vsto/troubleshooting-office-solution-deployment.md)
