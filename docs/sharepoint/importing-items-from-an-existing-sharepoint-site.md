---
title: Importation d’éléments à partir d’un site SharePoint existant | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.WSPImport.SelectionDependency
- VS.SharepointTools.WSPImport.SpecifyProjectSource
- VS.SharePointTools.WSPImport.SelectionItemsToImport
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, importing .wsp files
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9c2703bfdd4f47281a1fc19060cb69f8b312e7d2
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970559"
---
# <a name="import-items-from-an-existing-sharepoint-site"></a>Importer des éléments à partir d’un site SharePoint existant
  Le modèle de projet Importer le package de solution SharePoint vous permet de réutiliser des éléments tels que des types de contenu et des champs à partir de sites SharePoint existants dans une nouvelle solution SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Vous pouvez exécuter la plupart des solutions importées sans aucune modification, mais il existe certaines restrictions et complications à prendre en compte, en particulier si vous modifiez des éléments après les avoir importés.

> [!NOTE]
> Pour importer des flux de travail réutilisables, utilisez le modèle de projet Importer le flux de travail réutilisable. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Instructions pour l’importation de flux de travail réutilisables](../sharepoint/guidelines-for-importing-reusable-workflows.md).

## <a name="supported-sharepoint-solutions"></a>Solutions SharePoint prises en charge
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] prend entièrement en charge l’importation de solutions créées dans [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] et [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] ne prend pas en charge l’importation de solutions créées dans les applications suivantes :

- [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]

- [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]

- [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]

- Microsoft SharePoint Designer 2007

- [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]

  Bien que vous puissiez généralement importer des solutions créées par ces applications, cette fonctionnalité n’est ni testée, ni prise en charge.

## <a name="item-import-restrictions"></a>Restrictions relatives à l’importation d’éléments
 Bien que la plupart des éléments SharePoint puissent être importés à partir d’un fichier *. wsp* existant, les éléments suivants ne sont pas pris en charge et peuvent nécessiter des modifications pour fonctionner correctement :

- Entités BDC

- Éléments d’association de flux de travail de code

- Flux de travail de code

- Composants Visual Web Parts (.ascx)

- Services Web (*. asmx*)

- Liaisons de type de contenu

- Récepteurs d’événements

- Définitions de listes (modèles)

- Définitions de sites

  Lorsque vous exportez une solution à partir de [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] ou [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] , ces éléments sont exclus automatiquement du fichier *. wsp* . Toutefois, les autres fichiers *. wsp* générés à partir d’outils non pris en charge peuvent contenir ces éléments. (Voir « Solutions SharePoint prises en charge » plus haut dans cette rubrique.)

## <a name="what-happens-when-you-import-a-solution"></a>Que se passe-t-il lorsque vous importez une solution ?
 Lorsque vous importez une solution avec le modèle importer le package de solution SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] copie tout le contenu du fichier *. wsp* et tente de rapprocher et de conserver le nombre d’associations et de références entre les éléments importés et leurs fichiers, le cas échéant.

 Tous les éléments importés sont copiés dans des dossiers correspondants dans l’ **Explorateur de solutions**. Par exemple, les types de contenu apparaissent sous le dossier **Types de contenu** et les instances de listes apparaissent sous **Instances de listes**. Les fichiers associés à un élément importé sont également copiés dans le dossier de l’élément. Par exemple, une instance de liste importée comprend ses modules, formulaires et pages ASPX.

### <a name="dependent-items"></a>Éléments dépendants
 Si vous sélectionnez un élément dans l’Assistant Importer le package de solution SharePoint, mais pas ses éléments dépendants, une boîte de message vous signale que les éléments dépendants doivent aussi être sélectionnés avant l’importation.

### <a name="what-are-features"></a>Que sont les fonctionnalités ?
 Les utilisateurs de SharePoint Designer peuvent observer la présence de fichiers inattendus, appelés *fonctionnalités*, dans leurs solutions importées dans l’ **Explorateur de solutions.** Les fonctionnalités existaient dans la solution SharePoint Designer, mais elles étaient masquées. Elles sont désormais visibles dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

 Les fonctionnalités sont des conteneurs d’éléments SharePoint. Chaque fonctionnalité conserve une référence à chaque élément qu’elle contient, comme les types de contenu et les définitions de listes. Lorsque vous importez votre solution, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] configure des fonctionnalités pour tous les éléments importés et tente de conserver les relations entre les fonctionnalités et les éléments pour les fichiers. Tous les fichiers dont les références n’ont pas pu être résolues sont placés dans le dossier **Autres fichiers importés** .

 Pour plus d’informations sur les fonctionnalités, consultez [développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md) et [utiliser des fonctionnalités](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14)).

### <a name="handle-special-cases"></a>Gérer les cas spéciaux
 Dans certains cas, Visual Studio ne peut pas rapprocher un élément de ses fichiers dépendants. Tous les fichiers que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] n’a pas pu résoudre apparaissent sous le dossier **Autres fichiers importés**. En outre, leurs propriétés **DeploymentType** prennent la valeur **NoDeployment** pour qu’ils ne soient pas déployés avec la solution.

 Par exemple, si vous importez la définition de liste ExpenseForms, une définition de liste portant ce nom apparaît sous le dossier **définitions de liste** dans **Explorateur de solutions** , ainsi que ses fichiers de *Elements.xml* et de *Schema.xml* . Toutefois, ses formulaires ASPX et HTML associés peuvent être placés dans un dossier nommé **ExpenseForms** sous le dossier **Autres fichiers importés** . Pour terminer l’importation, déplacez ces fichiers sous la définition de liste ExpenseForms dans l’ **Explorateur de solutions** et modifiez la propriété **DeploymentType** de chaque fichier de **NoDeployment** en **ElementFile**.

 Lorsque vous importez des récepteurs d’événements, le fichier *Elements.xml* est copié à l’emplacement correct, mais vous devez inclure manuellement l’assembly dans le package de solution pour qu’il soit déployé avec la solution. [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)] pour ce faire, consultez [Comment : ajouter et supprimer des assemblys supplémentaires](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Quand vous importez des flux de travail, les formulaires InfoPath sont copiés dans le dossier **Autres fichiers importés** . Si le fichier *. wsp* contient un modèle Web, il est défini comme page de démarrage dans **Explorateur de solutions**.

## <a name="import-fields-and-property-bags"></a>Importer des champs et des conteneurs de propriétés
 Lorsque vous importez une solution comportant plusieurs champs, toutes les définitions de champs distinctes sont fusionnées dans un seul *Elements.xml* fichier sous un nœud dans **Explorateur de solutions** appelés **champs**. De même, toutes les entrées de conteneur de propriétés sont fusionnées dans un fichier de *Elements.xml* sous un nœud appelé **PropertyBags**.

 Dans SharePoint, les champs sont des colonnes d’un type de données spécifié, tel que texte, valeur booléenne ou recherche. Pour plus d’informations, consultez [Bloc de construction : Colonnes et types de champs](/previous-versions/office/developer/sharepoint-2010/ee535893(v=office.14)). Les conteneurs des propriétés vous permettent d’ajouter des propriétés à toutes sortes d’objets dans SharePoint, d’une batterie de serveurs entière à une simple liste sur un site SharePoint. Ils sont implémentés en tant que table de hachage de noms et de valeurs de propriétés. Pour plus d’informations, consultez [Gestion de la configuration de SharePoint](/previous-versions/msp-n-p/ff647766(v=pandp.10)) ou [Paramètres des conteneurs des propriétés SharePoint](https://archive.codeplex.com/?p=pbs).

## <a name="delete-items-in-the-project"></a>Supprimer des éléments dans le projet
 La plupart des éléments dans les solutions SharePoint ont un ou plusieurs éléments dépendants. Par exemple, les instances de listes dépendent des types de contenu et les types de contenu dépendent des champs. Une fois que vous avez importé une solution SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ne vous signale les éventuels problèmes de référence si vous supprimez un élément dans la solution, mais pas ses éléments dépendants, que lorsque vous tentez de déployer la solution. Par exemple, si une solution importée comporte une instance de liste qui dépend d’un type de contenu et que vous supprimez ce type de contenu, une erreur peut se produire pendant le déploiement. L’erreur se produit si l’élément dépendant n’est pas présent sur le serveur SharePoint. De même, si un élément supprimé a également un conteneur de propriétés associé, supprimez les entrées de ce conteneur de propriétés du fichier de *Elements.xml* **PropertyBags** . Ainsi, si vous supprimez des éléments d’une solution importée et que des erreurs de déploiement se produisent, vérifiez si des éléments dépendants doivent également être supprimés.

## <a name="restore-missing-feature-attributes"></a>Restaurer les attributs des fonctionnalités manquantes
 Lors de l’importation de solutions, certains attributs de fonctionnalités facultatifs sont omis du manifeste de fonctionnalité importé. Si vous souhaitez restaurer ces attributs dans le nouveau fichier de fonctionnalité, identifiez les attributs manquants en comparant le fichier de fonctionnalité d’origine au nouveau manifeste de fonctionnalité et suivez les instructions de la rubrique [How to : Customize a SharePoint Feature](../sharepoint/how-to-customize-a-sharepoint-feature.md).

## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>La détection des conflits de déploiement n’est pas effectuée sur les instances de listes intégrées
 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] n’effectue pas de détection des conflits de déploiement sur les instances de listes intégrées (c’est-à-dire les instances de listes par défaut fournies avec SharePoint). La non-détection des conflits a pour but d’éviter le remplacement des instances de listes intégrées dans SharePoint. Les instances de listes intégrées sont toujours déployées ou mises à jour, mais ne sont jamais supprimées ou remplacées. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Résoudre les problèmes d’empaquetage et de déploiement SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

## <a name="import-sharepoint-server-2010-workflows"></a>Importer des flux de travail SharePoint Server 2010
 Si vous importez un flux de travail créé dans [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)], il ne s’exécute pas correctement une fois déployé. Le flux de travail ne s’exécute pas correctement, car certains assemblys sont manquants et les flux de travail  [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] contiennent des formulaires InfoPath qui ne sont pas pris en charge actuellement dans les solutions de flux de travail [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Toutefois, les flux de travail [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] importés peuvent fonctionner correctement après quelques corrections, comme l’ajout de références aux assemblys [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] et la reconnexion des formulaires InfoPath. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Importation de flux de travail SharePoint Server 2010](/sharepoint/dev/).

## <a name="item-name-character-limit"></a>Limite de caractères de nom d’élément
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a une limite de 260 caractères pour le nom de projet et les noms des éléments de projet, chemin d’accès compris. Pendant l’importation d’une solution, si un nom d’élément dépasse cette limite, l’erreur suivante s’affiche :

 **Le chemin d’accès spécifié, le nom de fichier ou les deux sont trop longs. Le nom de fichier complet doit être inférieur à 260 caractères, et le nom du répertoire doit contenir moins de 248 caractères.**

 Quand cette erreur se produit, l’élément n’est pas créé. Ce problème se produit le plus souvent avec les modules importés. Pour l’éviter, procédez comme suit :

- Utilisez des noms courts pour vos projets quand vous les entrez dans la boîte de dialogue **Ajouter un nouveau projet** .

- Créez le projet dans un emplacement le plus près possible du dossier racine, afin de raccourcir le chemin d’accès.

## <a name="the-sharepointproductversion-attribute"></a>Attribut SharePointProductVersion
 Si vous importez une solution créée dans une version antérieure de SharePoint telle que [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] ou [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], vous devez soit remplacer la valeur de l’attribut SharePointProductVersion dans le manifeste du package par 12.0, soit insérer un contrôle de gestionnaire de scripts dans toutes les pages web importées et conserver la valeur 14.0 pour l’attribut SharePointProductVersion. Autrement, les formulaires web importés ne s’afficheront pas dans SharePoint.

### <a name="background"></a>Arrière-plan
 Les solutions dans [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] et [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] incluent un attribut nommé SharePointProductVersion. SharePoint utilise cet attribut dans ses manifestes de packages pour déterminer la version de SharePoint pour laquelle la solution est conçue. Les deux valeurs valides sont 12.0 et 14.0. La valeur 12.0 indique que l’élément est conçu pour [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] ou [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]. La valeur 14.0 indique que l’élément est conçu pour [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] ou [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

 Pour renforcer la sécurité lors du rendu des pages ASPX, [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] et [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] exigent que toutes les pages ASPX ou pages maîtres contiennent un contrôle de gestionnaire de scripts. Pour plus d’informations sur le gestionnaire de scripts, consultez [Vue d’ensemble du contrôle ScriptManager](/previous-versions/bb398863(v=vs.140)). Le contrôle de gestionnaire de scripts n’étant pas disponible dans [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] et [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], vous devez en ajouter un à toute page [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] ou [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] qui est mise à niveau vers [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] ou [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]. Les pages ASPX qui utilisent une page maître standard ne nécessitent pas de contrôle de gestionnaire de scripts, car un contrôle de ce type a déjà été ajouté à la page maître standard. En revanche, les pages ASPX qui n’utilisent pas de page maître ou qui utilisent une page maître personnalisée doivent ajouter un contrôle de script pour fonctionner dans [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] ou [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

 L’absence de contrôle de gestionnaire de scripts peut être problématique quand vous importez un projet [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] ou [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] dans [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], car l’attribut SharePointProductVersion de tous les nouveaux projets a la valeur 14.0. Si vous déployez un projet mis à niveau comportant un formulaire web sans gestionnaire de scripts, le formulaire ne s’affichera pas dans SharePoint.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : importer des éléments à partir d’un site SharePoint existant](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)
- [Instructions pour l’importation de flux de travail réutilisables](../sharepoint/guidelines-for-importing-reusable-workflows.md)
- [Procédure pas à pas : importer un flux de travail réutilisable SharePoint Designer dans Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
- [Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
