---
title: Considérations de sécurité spécifiques pour les solutions Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting Office development in Visual Studio, security
- trusted code [Office development in Visual Studio]
- blocked code [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], object model guard
- malicious code [Office development in Visual Studio]
- Outlook object model guard [Office development in Visual Studio]
- security [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 33d827efa7dcc4e5590b4bc45fb0d6bd3fbe1432
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955540"
---
# <a name="specific-security-considerations-for-office-solutions"></a>Considérations de sécurité spécifiques pour les solutions Office
  Les fonctionnalités de sécurité fournies par Microsoft .NET Framework et Microsoft Office peuvent renforcer la protection contre diverses menaces possibles dans les solutions Office. Cette rubrique décrit certaines de ces menaces et fournit des recommandations pour vous protéger contre elles. Elle inclut également des informations sur l’impact des paramètres de sécurité Microsoft Office sur les solutions Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>Code de confiance est réaffecté dans un nouveau document  
 Une personne malveillante peut prendre du code de confiance destiné à un usage particulier, par exemple, au téléchargement d’informations personnelles pour une candidature à un emploi et le réutiliser dans un autre document, comme une feuille de calcul. Le code ne sait pas que le document d’origine n’est pas en cours d’exécution et peut entraîner d’autres menaces, comme la divulgation des informations personnelles ou l’exécution de code avec des privilèges accrus, quand un autre utilisateur l’ouvre. Vous pouvez également l’attaquant peut modifier les données dans la feuille de calcul telles que, lorsque envoyée à la victime, elle fonctionne de manière inattendue. En modifiant les valeurs, les formules ou les caractéristiques de présentation d’une feuille de calcul liée à du code, un utilisateur malveillant peut attaquer un autre utilisateur en envoyant un fichier modifié. D’autres utilisateurs peuvent également accéder à des informations qu’ils ne sont pas supposés consulter en modifiant des valeurs dans la feuille de calcul.  
  
 Étant donné que l’emplacement de l’assembly et l’emplacement du document doivent avoir suffisamment de preuves pour s’exécuter, cette attaque n’est pas facile à monter. Par exemple, les documents dans les pièces jointes à des messages électroniques ou sur des serveurs intranet non fiables n’ont pas les autorisations suffisantes pour s’exécuter.  
  
 Pour qu’une telle attaque soit possible, le code lui-même doit être écrit de façon à prendre des décisions en fonction de données potentiellement non fiables. Un exemple consiste à créer une feuille de calcul qui comporte une cellule masquée qui contient le nom d’un serveur de base de données. L’utilisateur soumet la feuille de calcul à une page ASPX qui essaie de se connecter à ce serveur à l’aide de l’authentification SQL et d’un mot de passe SA codé en dur. Une personne malveillante peut remplacer le contenu de la cellule masquée par un autre nom d’ordinateur et obtenir le mot de passe SA. Pour éviter ce problème, ne codez jamais en dur les mots de passe et vérifiez toujours les ID de serveur par rapport à la liste interne des serveurs reconnus comme fiables avant d’accéder au serveur.  
  
### <a name="recommendations"></a>Recommandations  
  
-   Validez toujours l’entrée et les données, qu’elles proviennent de l’utilisateur, du document, d’une base de données, d’un service web ou de toute autre source.  
  
-   Exposez prudemment les types particuliers de fonctionnalités, comme l’obtention de données privilégiées au nom de l’utilisateur et leur placement dans une feuille de calcul non protégée.  
  
-   Selon le type d’application, il convient de vérifier que le document d’origine est en cours d’exécution avant d’exécuter du code, quel qu’il soit. Par exemple, vérifiez qu’il s’exécute à partir d’un document stocké dans un emplacement connu et sécurisé.  
  
-   Il peut s’avérer judicieux d’afficher un avertissement à l’ouverture du document si votre application effectue des actions privilégiées. Par exemple, vous pouvez créer un écran de démarrage ou une boîte de dialogue de démarrage indiquant que l’application accède à des informations personnelles et demander à l’utilisateur de choisir de continuer ou d’annuler. Si un utilisateur final obtient un tel avertissement d’un document apparemment innocent, il est en mesure de quitter l’application avant de compromettre quoi que ce soit.  
  
## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>Code bloqué par le modèle objet Outlook  
 Microsoft Office peut empêcher le code d’utiliser des propriétés, méthodes et objets particuliers dans le modèle objet. En limitant l’accès à ces objets, Outlook permet d’éviter les virus et vers de messagerie à partir de l’utilisation du modèle objet à des fins malveillantes. Cette fonctionnalité de sécurité porte le nom de module de protection du modèle objet Outlook. Si un complément, VSTO tente d’utiliser une propriété ou méthode restreinte alors que le dispositif object model guard est activé, Outlook affiche un avertissement de sécurité qui permet à l’utilisateur d’arrêter l’opération ou permet à l’utilisateur d’octroyer l’accès à la propriété ou méthode pendant une période limitée de t IME. Si l’utilisateur arrête l’opération, les compléments VSTO Outlook créés à l’aide de solutions Office dans Visual Studio lèvent une <xref:System.Runtime.InteropServices.COMException>.  
  
 Le module de protection du modèle objet peut influer sur les compléments VSTO de différentes façons, selon qu’Outlook est utilisé avec Microsoft Exchange Server ou non :  
  
- Si Outlook n’est pas utilisé avec Exchange, un administrateur peut activer ou désactiver le module de protection du modèle objet pour tous les compléments VSTO existant sur l’ordinateur.  
  
- Si Outlook est utilisé avec Exchange, un administrateur peut activer ou désactiver le module de protection du modèle objet pour tous les compléments VSTO de l’ordinateur ou l’administrateur peut spécifier que certains compléments VSTO peuvent s’exécuter sans rencontrer le module de protection du modèle objet. Les administrateurs peuvent également modifier le comportement du module de protection du modèle objet dans certaines zones du modèle objet. Par exemple, les administrateurs peuvent permettre automatiquement aux compléments VSTO envoyer un e-mail par programmation, même si le dispositif object model guard est activé.  
  
  À partir d’Outlook 2007, le comportement du module de protection du modèle objet a été modifié pour améliorer l’expérience du développeur et de l’utilisateur tout en sécurisant Outlook. Pour plus d’informations, consultez [Code des modifications de sécurité dans Outlook 2007](http://go.microsoft.com/fwlink/?LinkId=73429).  
  
### <a name="minimize-object-model-guard-warnings"></a>Réduire les avertissements de protection du modèle objet  
 Pour éviter les avertissements de sécurité quand vous utilisez des propriétés et méthodes restreintes, assurez-vous que votre complément VSTO obtient des objets Outlook à partir du champ `Application` de la classe `ThisAddIn` dans votre projet. Pour plus d’informations sur ce champ, consultez [programme VSTO Add-ins](../vsto/programming-vsto-add-ins.md).  
  
 Seuls les objets Outlook obtenus à partir de cet objet peuvent être approuvés par le module de protection du modèle objet. En revanche, les objets obtenus à partir d’un nouvel objet `Microsoft.Office.Interop.Outlook.Application` ne sont pas approuvés et les propriétés et méthodes restreintes déclenchent des avertissements de sécurité si le module de protection du modèle objet est activé.  
  
 L’exemple de code suivant affiche un avertissement de sécurité si le module de protection du modèle objet est activé. La propriété `To` de la classe `Microsoft.Office.Interop.Outlook.MailItem` est restreinte par le module de protection du modèle objet. Le `Microsoft.Office.Interop.Outlook.MailItem` objet n’est pas approuvé car le code l’obtient à partir d’un `Microsoft.Office.Interop.Outlook.Application` qui est créé à l’aide la **nouvelle** opérateur, au lieu de l’obtenir à partir la `Application` champ.  
  
 [!code-csharp[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#1)]
 [!code-vb[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#1)]  
  
 L’exemple de code suivant montre comment utiliser restreint à la propriété d’un `Microsoft.Office.Interop.Outlook.MailItem` objet qui est approuvé par le dispositif object model guard. Le code utilise le champ `Application` approuvé pour obtenir l’objet `Microsoft.Office.Interop.Outlook.MailItem`.  
  
 [!code-csharp[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#2)]
 [!code-vb[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#2)]  
  
> [!NOTE]  
>  Si Outlook est utilisé avec Exchange, alors l’obtention de tous les objets Outlook à partir de `ThisAddIn.Application` ne garantit pas que votre complément VSTO est en mesure d’accéder à l’ensemble du modèle objet Outlook. Par exemple, si un administrateur Exchange configure Outlook automatiquement refuser toutes les tentatives d’accès aux adresses via le modèle objet Outlook, puis Outlook n’autorisera pas l’exemple de code précédent à accéder à la propriété, même si l’exemple de code utilise la confiance `ThisAddIn.Application` champ.  
  
### <a name="specify-which-add-ins-to-trust-when-using-exchange"></a>Spécifiez les compléments à approuver lors de l’utilisation d’Exchange  
 Quand Outlook est utilisé avec Exchange, les administrateurs peuvent spécifier que certains compléments VSTO peuvent s’exécuter sans rencontrer le module de protection du modèle objet. Les compléments VSTO Outlook créés à l’aide de solutions Office dans Visual Studio ne peuvent pas être approuvés individuellement. Ils peuvent uniquement l’être en tant que groupe.  
  
 Outlook approuve un complément VSTO selon un code de hachage de la DLL de point d’entrée de la VSTO Add-in. Tous les Outlook VSTO Add-ins qui ciblent le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] utilisent la même DLL de point d’entrée (*VSTOLoader.dll*). Cela signifie que si un administrateur approuve un complément qui cible le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] à s’exécuter sans rencontrer le dispositif object model guard, puis tous les autres compléments VSTO qui ciblent le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sont également approuvés. Pour plus d’informations sur l’approbation de compléments VSTO spécifiques pour une exécution sans rencontrer le module de protection du modèle objet, consultez [Spécifier la méthode utilisée par Outlook pour gérer les fonctionnalités de prévention antivirus](http://go.microsoft.com/fwlink/?LinkId=128773).  
  
## <a name="permission-changes-do-not-take-effect-immediately"></a>Modifications de permission ne prennent pas effet immédiatement  
 Si l’administrateur ajuste les autorisations d’un document ou d’un assembly, les utilisateurs doivent quitter, puis redémarrer toutes les applications Office pour que ces modifications soient appliquées.  
  
 D’autres applications qui hébergent des applications Microsoft Office peuvent également empêcher l’application des nouvelles autorisations. Les utilisateurs doivent quitter toutes les applications qui utilisent Office, hébergées ou autonomes, quand des stratégies de sécurité sont modifiées.  
  
## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Paramètres du centre de confiance dans le système Microsoft Office n’affectent pas les compléments ou personnalisations au niveau du document  
 Les utilisateurs peuvent empêcher le chargement de compléments VSTO en définissant une option dans le **Centre de gestion de la confidentialité**. Toutefois, les compléments VSTO et les personnalisations au niveau du document créés à l’aide de solutions Office dans Visual Studio ne sont pas concernés par ces paramètres d’approbation.  
  
 Si l’utilisateur empêche le chargement de compléments VSTO à l’aide du **Centre de gestion de la confidentialité**, les types suivants de compléments VSTO ne se chargent pas :  
  
- Compléments VSTO COM gérés et non gérés.  
  
- Documents dynamiques gérés et non gérés.  
  
- Compléments VSTO Automation gérés et non gérés.  
  
- Composants de données en temps réel gérés et non gérés.  
  
  Les procédures suivantes décrivent la manière dont les utilisateurs peuvent utiliser le **Centre de gestion de la confidentialité** pour limiter le chargement de compléments VSTO dans Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] et Microsoft Office 2010. Ces procédures n’affectent pas les compléments VSTO ni les personnalisations créés à l’aide des outils de développement Office dans Visual Studio.  
  
#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-includeoffice15shortvstoincludesoffice-15-short-mdmd-applications"></a>Pour désactiver les compléments VSTO dans les applications Microsoft Office 2010 et Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]  
  
1.  Choisissez l’onglet **Fichier** .  
  
2.  Choisissez le bouton *Options de* **nom_application** .  
  
3.  Dans le volet des catégories, choisissez **Centre de gestion de la confidentialité**.  
  
4.  Dans le volet d’informations, choisissez **Paramètres du Centre de gestion de la confidentialité**.  
  
5.  Dans le volet des catégories, choisissez **Compléments**.  
  
6.  Dans le volet d’informations, sélectionnez **Exiger la signature des compléments d’applications par un éditeur approuvé** ou **Désactiver tous les compléments d’applications**.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisez les solutions Office](../vsto/securing-office-solutions.md)  
