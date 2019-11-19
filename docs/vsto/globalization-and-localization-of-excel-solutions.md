---
title: Globalisation et localisation de solutions Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], configuring
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f37ddcbbd3145fc96cd8081d7a1df524ef7ea8ec
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986053"
---
# <a name="globalization-and-localization-of-excel-solutions"></a>Globalisation et localisation de solutions Excel
  Cette section contient des informations sur les considérations spéciales concernant les solutions Microsoft Office Excel appelées à être exécutées sur des ordinateurs dont les paramètres Windows sont autres qu’anglais. La plupart des aspects de la globalisation et de la localisation des solutions Microsoft Office sont les mêmes que ceux que vous rencontrez quand vous créez d’autres types de solutions à l’aide de Visual Studio. Pour obtenir des informations générales, consultez [globalisation et localisation d’applications](../ide/globalizing-and-localizing-applications.md).

 Par défaut, les contrôles hôtes dans Microsoft Office Excel fonctionnent correctement dans tous les paramètres régionaux Windows, dans la mesure où l’ensemble des données passées ou manipulées avec du code managé présentent une mise en forme Anglais (États-Unis). Dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], ce comportement est contrôlé par le Common Language Runtime (CLR).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="format-data-in-excel-with-various-regional-settings"></a>Mettre en forme des données dans Excel avec différents paramètres régionaux
 Vous devez mettre en forme toutes les données ayant une mise en forme sensible aux paramètres régionaux, telles que les dates et les devises, en utilisant le format de données Anglais (États-Unis) (ID de paramètres régionaux 1033) avant de les passer à Microsoft Office Excel ou de lire ces données à partir du code de votre projet Office.

 Par défaut, quand vous développez une solution Office dans Visual Studio, le modèle objet Excel attend la mise en forme de données correspondant à l’ID de paramètres régionaux 1033 (c’est ce que l’on appelle également verrouiller le modèle objet sur l’ID de paramètres régionaux 1033). Ce comportement correspond au mode de fonctionnement de Visual Basic pour Applications. Cependant, vous pouvez modifier ce comportement dans vos solutions Office.

### <a name="understand-how-the-excel-object-model-always-expects-locale-id-1033"></a>Comprendre comment le modèle objet Excel attend toujours l’ID de paramètres régionaux 1033
 Par défaut, les solutions Office que vous créez à l’aide de Visual Studio ne sont pas affectées par les paramètres régionaux de l’utilisateur final et se comportent toujours comme si les paramètres régionaux étaient Anglais (États-Unis). Par exemple, si vous obtenez ou définissez la propriété <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> dans Excel, les données doivent être mises en forme comme l’attend l’ID de paramètres régionaux 1033. Si vous utilisez un autre format de données, vous risquez d’obtenir des résultats inattendus.

 Même si vous utilisez le format Anglais (États-Unis) pour les données passées ou manipulées par du code managé, Excel interprète et affiche les données correctement en fonction des paramètres régionaux de l’utilisateur final. Excel peut mettre correctement en forme les données, car le code managé passe l’ID de paramètres régionaux 1033 en même temps que les données, ce qui indique que les données sont au format Anglais (États-Unis) et qu’elles doivent donc être remises en forme en fonction des paramètres régionaux de l’utilisateur.

 Par exemple, si les utilisateurs finaux ont défini leurs options régionales sur les paramètres régionaux Allemand (Allemagne), ils s’attendent à ce que la date du 29 juin 2005 soit mise en forme de de cette façon : 29.06.2005. Or, si votre solution passe la date à Excel sous forme de chaîne, vous devez mettre en forme la date selon le format Anglais (États-Unis) : 6/29/2005. Si la cellule est mise en forme en tant que cellule de date, Excel affiche la date au format Allemand (Allemagne).

### <a name="pass-other-locale-ids-to-the-excel-object-model"></a>Passer d’autres ID de paramètres régionaux au modèle objet Excel
 Le Common Language Runtime (CLR) passe automatiquement l’ID de paramètres régionaux 1033 à toutes les méthodes et propriétés du modèle objet Excel qui acceptent les données sensibles aux paramètres régionaux. Il n’y a aucun moyen de modifier ce comportement automatiquement pour tous les appels à destination du modèle objet. Cependant, vous pouvez passer un autre ID de paramètres régionaux à une méthode spécifique en utilisant <xref:System.Type.InvokeMember%2A> pour appeler la méthode et en passant l’ID de paramètres régionaux au paramètre *culture* de la méthode.

## <a name="localize-document-text"></a>Localiser le texte du document
 Il est probable que le document, le modèle ou le classeur de votre projet contient du texte statique, qui doit être localisé séparément à partir de l’assembly et d’autres ressources managées. Une façon simple de procéder consiste à copier le document et à traduire le texte en utilisant Microsoft Office Word ou Microsoft Office Excel. Cette procédure fonctionne même si vous n’apportez pas de modifications au code, car vous pouvez lier n’importe quel nombre de documents à un même assembly.

 Vous devez quand même vous assurer que les parties de votre code qui interagissent avec le texte du document continuent de correspondre à la langue du texte et que les signets, plages nommées et autres champs d’affichage s’accommodent de toute nouvelle mise en forme du document Office qui s’avérait nécessaire pour s’adapter à la grammaire et à la longueur de texte différentes. Pour les modèles de document qui contiennent peu de texte, vous pouvez envisager de stocker le texte dans des fichiers de ressources, puis de le charger au moment de l’exécution.

### <a name="text-direction"></a>Orientation du texte
 Dans Excel, vous pouvez définir une propriété de la feuille de calcul pour afficher le texte de droite à gauche. Les contrôles hôtes, ou tout contrôle ayant une propriété `RightToLeft`, qui est placé sur le concepteur correspondent automatiquement à ces paramètres au moment de l’exécution. Word n’a pas de paramètre de document pour le texte bidirectionnel (vous modifiez simplement l’alignement du texte). par conséquent, les contrôles ne peuvent pas être mappés à ce paramètre. Au lieu de cela, vous devez définir l’alignement du texte pour chaque contrôle. Il est possible d’écrire du code qui parcoure tous les contrôles et les force à afficher le texte de droite à gauche.

### <a name="change-culture"></a>Modifier la culture
 Votre code de personnalisation au niveau du document partage généralement le thread d’interface utilisateur principal d’Excel. De ce fait, toute modification que vous apportez à la culture du thread affecte tout ce qui s’exécute sur celui-ci ; la modification ne se limite pas à votre personnalisation.

 Les contrôles Windows Forms sont initialisés avant que l’application hôte démarre les compléments VSTO de niveau application. En pareil cas, la culture doit être modifiée avant de définir les contrôles d’interface utilisateur.

## <a name="install-the-language-packs"></a>Installer les modules linguistiques
 Si vous n’avez pas les paramètres Anglais pour Windows, vous pouvez installer les modules linguistiques [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pour voir les messages de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dans la même langue que celle de Windows. Si des utilisateurs finals n’exécutent pas vos solutions avec des paramètres Anglais pour Windows, ils doivent disposer du module linguistique approprié pour voir les messages du runtime dans la même langue que celle de Windows. Les modules linguistiques [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sont disponibles dans le [Centre de téléchargement Microsoft](https://www.microsoft.com/download).

 Par ailleurs, les modules linguistiques .NET Framework sont nécessaires pour les messages ClickOnce. Les modules linguistiques .NET Framework sont disponibles dans le [Centre de téléchargement Microsoft](https://www.microsoft.com/download).

## <a name="regional-settings-and-excel-com-calls"></a>Paramètres régionaux et appels COM Excel
 Chaque fois qu’un client managé appelle une méthode sur un objet COM et qu’il doit passer des informations spécifiques à la culture, il utilise la propriété <xref:System.Globalization.CultureInfo.CurrentCulture%2A> (paramètres régionaux) qui correspond aux paramètres régionaux du thread actif. Par défaut, les paramètres régionaux du thread actif sont hérités des paramètres régionaux de l’utilisateur. Cependant, quand vous effectuez un appel dans le modèle objet Excel à partir d’une solution Excel créée à l’aide des outils de développement Office dans Visual Studio, le format de données Anglais (États-Unis) (ID de paramètres régionaux 1033) est passé automatiquement au modèle objet Excel. Vous devez mettre en forme toutes les données ayant une mise en forme sensible aux paramètres régionaux, telles que les dates et les devises, en utilisant le format de données Anglais (États-Unis) avant de les passer à Microsoft Office Excel ou de lire ces données à partir du code de votre projet.

## <a name="considerations-for-storing-data"></a>Considérations relatives au stockage des données
 Pour assurer une interprétation et une lecture correctes de vos données, vous devez aussi savoir que des problèmes peuvent survenir quand une application stocke des données (par exemple, les formules dans les feuilles de calcul Excel) dans des littéraux de chaîne (codés en dur) et non dans des objets fortement typés. Vous devez utiliser des données mises en forme dans un style indépendant de la culture ou au format Anglais (États-Unis) (valeur LCID 1033).

### <a name="applications-that-use-string-literals"></a>Applications qui utilisent des littéraux de chaîne
 Parmi les valeurs qui peuvent être codées en dur figurent les littéraux de date écrits au format Anglais (États-Unis) et les formules de feuille de calcul Excel qui contiennent des noms de fonctions localisés. Une chaîne codée en dur contenant un nombre tel que « 1,000 » est une autre possibilité ; dans certaines cultures, ce nombre est interprété comme un millier, mais dans d’autres, il représente « un virgule zéro ». Les calculs et les comparaisons effectués sur un format incorrect peuvent produire des données incorrectes.

 Excel interprète les chaînes conformément au LCID qui est passé avec celles-ci. Cela peut poser un problème si le format de la chaîne ne correspond pas au LCID passé. Les solutions Excel créées à l’aide des outils de développement Office dans Visual Studio utilisent le LCID 1033 (en-US) au moment de passer toutes les données. Excel affiche les données en fonction des paramètres régionaux et de la langue de l’interface utilisateur Excel. Visual Basic pour Applications (VBA) fonctionne aussi de cette façon ; les chaînes sont mises en forme au format en-US et VBA passe presque toujours 0 (indépendant de la langue) en guise de LCID. Par exemple, le code VBA suivant affiche une valeur correctement mise en forme pour le 12 mai 2004, conformément aux paramètres régionaux de l’utilisateur actuel :

```vb
'VBA
Application.ActiveCell.Value2 = "05/12/04"
```

 Ce même code, quand il est utilisé dans une solution créée à l’aide des outils de développement Office dans Visual Studio et passé à Excel via COM Interop, produit les mêmes résultats quand la date est mise en forme dans le style en-US.

 Exemple :

 [!code-vb[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#6)]
 [!code-csharp[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#6)]

 Vous avez tout intérêt à utiliser des données fortement typées à la place de littéraux de chaîne chaque fois que vous en avez la possibilité. Par exemple, au lieu de stocker une date dans un littéral de chaîne, stockez-la sous forme de <xref:System.Double>, puis convertissez-le en objet <xref:System.DateTime> pour la manipulation.

 L’exemple de code suivant prend une date entrée par un utilisateur dans la cellule A5, la stocke sous forme de <xref:System.Double>, puis le convertit en objet <xref:System.DateTime> pour l’afficher dans la cellule A7. La cellule A7 doit être mise en forme pour afficher une date.

 [!code-vb[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#7)]
 [!code-csharp[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#7)]

### <a name="excel-worksheet-functions"></a>Fonctions de feuille de calcul Excel
 Les noms de fonctions de feuille de calcul sont traduits en interne pour la plupart des versions linguistiques d’Excel. Toutefois, en raison de la langue et des problèmes de COM Interop potentiels, il est recommandé d’utiliser uniquement des noms de fonctions anglais dans votre code.

### <a name="applications-that-use-external-data"></a>Applications qui utilisent des données externes
 Tout code ouvrant ou utilisant des données externes, telles que des fichiers contenant des valeurs séparées par des virgules (fichiers CSV) exportés à partir d’un système hérité, peut aussi être affecté si ces fichiers sont exportés en utilisant un format en plus de « en-US ». Il se peut que l’accès à la base de données ne soit pas affecté, car toutes les valeurs sont censées être au format binaire, à moins que la base de données stocke les dates sous forme de chaînes ou exécute des opérations qui n’utilisent pas le format binaire. De même, si vous créez des requêtes SQL en utilisant des données à partir d’Excel, vous devrez peut-être vérifier qu’elles sont au format en-US, selon la fonction que vous utilisez.

## <a name="see-also"></a>Voir aussi

- [Comment : cibler l’interface utilisateur multilingue d’Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)