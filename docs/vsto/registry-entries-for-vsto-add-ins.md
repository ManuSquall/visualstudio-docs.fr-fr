---
title: Les entrées de Registre pour les Compléments VSTO | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- LoadBehavior entry
- add-ins [Office development in Visual Studio], registry entries
- registry keys [Office development in Visual Studio]
- application-level add-ins [Office development in Visual Studio], registry entries
- registry entries [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5e4c410a6f934c7b4fe4c6239bdfe07364af3152
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="registry-entries-for-vsto-add-ins"></a>Entrées de Registre pour les compléments VSTO
  Vous devez créer un ensemble spécifique d'entrées de Registre quand vous déployez des compléments VSTO créés à l'aide de Visual Studio. Ces entrées de Registre fournissent des informations qui permettent à l'application Microsoft Office de découvrir et de charger le complément VSTO.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Quand vous générez votre projet, Visual Studio crée ces entrées de Registre sur l'ordinateur de développement pour que vous puissiez facilement exécuter et déboguer le complément VSTO. Si vous utilisez ClickOnce pour déployer votre complément VSTO, les entrées de Registre sont automatiquement créées sur l'ordinateur de l'utilisateur final. Si vous utilisez Windows Installer pour déployer votre complément VSTO, vous devez configurer le projet InstallShield Limited Edition pour qu'il crée les entrées de Registre sur l'ordinateur de l'utilisateur final.  
  
 Pour plus d’informations sur la façon dont les entrées de Registre sont utilisées pendant le processus de chargement des compléments VSTO, consultez [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  Dans cette rubrique, le texte *ID du complément* représente l'ID unique de votre complément VSTO. Par défaut, l'ID est le nom de l'assembly de votre complément VSTO.  
  
## <a name="registering-vsto-add-ins-for-the-current-user-vs-all-users"></a>Inscription de compléments VSTO pour l'utilisateur actuel ou pour tous les utilisateurs  
 Quand un complément VSTO est installé, il peut être inscrit de deux façons :  
  
-   Pour l'utilisateur actuel uniquement (le complément VSTO n'est alors disponible que pour l'utilisateur connecté à l'ordinateur où le complément est installé). Dans ce cas, les entrées de Registre sont créées sous HKEY_CURRENT_USER.  
  
-   Pour tous les utilisateurs (tout utilisateur qui se connecte à l'ordinateur peut utiliser le complément VSTO). Dans ce cas, les entrées de Registre sont créées sous HKEY_LOCAL_MACHINE.  
  
 Tous les compléments VSTO que vous créez à l'aide de Visual Studio peuvent être inscrits pour l'utilisateur actuel. En revanche, ils ne peuvent être inscrits pour tous les utilisateurs que dans certains scénarios particuliers. Ces scénarios dépendent de la version de Microsoft Office installée sur l'ordinateur et de la façon dont le complément VSTO a été déployé.  
  
### <a name="microsoft-office-version"></a>Version de Microsoft Office  
 Les applications Office peuvent charger les compléments VSTO inscrits sous HKEY_LOCAL_MACHINE ou HKEY_CURRENT_USER.  
  
 Pour permettre le chargement des compléments VSTO inscrits sous HKEY_LOCAL_MACHINE, le package de mise à jour 976477 doit être installé sur les ordinateurs. Pour plus d’informations, consultez [http://go.microsoft.com/fwlink/?LinkId=184923](http://go.microsoft.com/fwlink/?LinkId=184923).  
  
### <a name="deployment-type"></a>Type de déploiement  
 Si vous utilisez ClickOnce pour déployer un complément VSTO, ce dernier ne peut être inscrit que pour l'utilisateur actuel. En effet, ClickOnce prend uniquement en charge la création de clés sous HKEY_CURRENT_USER. Si vous voulez inscrire un complément VSTO pour tous les utilisateurs d'un ordinateur, vous devez déployer ce complément à l'aide de Windows Installer. Pour plus d’informations sur ces types de déploiement, consultez [déploiement d’une Solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md) et [déploiement d’une Solution Office à l’aide de Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## <a name="registry-entries"></a>Entrées de Registre  
 Les entrées de Registre du complément VSTO nécessaires se trouvent sous la clé de Registre suivante pour toutes les applications, sauf Visio, où la *Racine* est HKEY_CURRENT_USER ou HKEY_LOCAL_MACHINE.  
  
 **Ensemble des applications sauf Visio**  
  
|version d'Office|Chemin d'accès de configuration|  
|--------------------|------------------------|  
|32 bits|*Racine*\Software\Microsoft\Office\\*nom de l’application*\Addins\\*ID du complément*|  
|64 bits|*Racine*\Software\Wow6432Node\Microsoft\Office\\*nom de l’application*\Addins\\*ID du complément*|  
  
 **Visio**  
  
|version d'Office|Chemin d'accès de configuration|  
|--------------------|------------------------|  
|32 bits|*Racine*\Software\Microsoft\Visio\Addins\\*ID du complément*|  
|64 bits|*Racine*\Software\Wow6432Node\Visio\Addins\\*ID du complément*|  
  
 Le tableau suivant répertorie les entrées sous cette clé de Registre.  
  
|Entrée|Type|Value|  
|-----------|----------|-----------|  
|**Description**|REG_SZ|Obligatoire. Brève description du complément VSTO.<br /><br /> Cette description s'affiche quand l'utilisateur sélectionne le complément VSTO dans le volet **Compléments** de la boîte de dialogue **Options** de l'application Microsoft Office.|  
|**FriendlyName**|REG_SZ|Obligatoire. Nom descriptif du complément VSTO qui s'affiche dans la boîte de dialogue **Compléments COM** de l'application Microsoft Office. La valeur par défaut est l'ID du complément VSTO.|  
|**LoadBehavior**|REG_DWORD|Obligatoire. Valeur qui spécifie le moment où l'application tente de charger le complément VSTO, ainsi que l'état actuel du complément VSTO (chargé ou non chargé).<br /><br /> Par défaut, cette entrée a la valeur 3, ce qui indique que le complément VSTO est chargé au démarrage. Pour plus d'informations, voir [LoadBehavior Values](#LoadBehavior). **Remarque :** si un utilisateur désactive le complément à VSTO, cette action modifie **LoadBehavior** dans la ruche de Registre HKEY_CURRENT_USER. Pour chaque utilisateur, la valeur de **LoadBehavior** dans la ruche HKEY_CURRENT_USER remplace la valeur par défaut **LoadBehavior** définie dans la ruche HKEY_LOCAL_MACHINE.|  
|**Manifest**|REG_SZ|Obligatoire. Chemin d'accès complet du manifeste de déploiement du complément VSTO. Le chemin d'accès peut être un emplacement sur l'ordinateur local, un partage réseau (UNC) ou un serveur web (HTTP).<br /><br /> Si vous utilisez Windows Installer pour déployer la solution, vous devez ajouter le préfixe **file:///** au chemin d'accès du **manifeste** . Vous devez également ajouter la chaîne  **&#124;vstolocal** (autrement dit, la barre verticale **&#124;** suivie **vstolocal**) à la fin de ce chemin d’accès. Cela permet de garantir que votre solution est chargée à partir du dossier d'installation, et non à partir du cache ClickOnce. Pour plus d'informations, consultez [Déploiement d’une solution Office à l’aide de Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md). **Remarque :** quand vous générez un complément, VSTO sur l’ordinateur de développement, Visual Studio ajoute automatiquement le  **&#124;vstolocal** chaîne pour cette entrée de Registre.|  
  
###  <a name="OutlookEntries"></a> Entrées du Registre des zones de formulaire Outlook  
 Si vous créez une zone de formulaire personnalisée dans un complément VSTO pour Outlook, des entrées de Registre supplémentaires sont utilisées pour inscrire la zone de formulaire dans Outlook. Ces entrées sont créées sous une autre clé de Registre pour chaque classe de message prise en charge par la zone de formulaire. Ces clés de Registre sont à l'emplacement suivant, où la *Racine* est HKEY_CURRENT_USER ou HKEY_LOCAL_MACHINE.  
  
 *Racine*\Software\Microsoft\Office\Outlook\FormRegions\\*message, classe*  
  
 Comme pour les autres entrées de Registre partagées par l'ensemble des compléments VSTO, Visual Studio crée les entrées de Registre de zones de formulaire sur l'ordinateur de développement au moment où vous générez votre projet. Si vous utilisez ClickOnce pour déployer votre complément VSTO, les entrées de Registre sont automatiquement créées sur l'ordinateur de l'utilisateur final. Si vous utilisez Windows Installer pour déployer votre complément VSTO, vous devez configurer le projet InstallShield Limited Edition pour qu'il crée les entrées de Registre sur l'ordinateur de l'utilisateur final.  
  
 Pour plus d’informations sur les entrées de Registre des zones de formulaire, consultez [spécifier l’emplacement d’une zone de formulaire dans un formulaire personnalisé](http://msdn.microsoft.com/library/office/ff868998.aspx). Pour plus d’informations sur les zones de formulaire Outlook, consultez [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
##  <a name="LoadBehavior"></a> LoadBehavior Values  
 Le **LoadBehavior** entrée sous le *racine*\Software\Microsoft\Office\\*nom de l’application*\Addins\\*complément ID* clé contient une combinaison d’opérations de bits de valeurs qui spécifient le comportement d’exécution de la macro complémentaire VSTO. Le bit d'ordre le plus bas (valeurs 0 et 1) indique si le complément VSTO est actuellement chargé ou non chargé. Les autres bits indiquent le moment où l'application tente de charger le complément VSTO.  
  
 En règle générale, l'entrée **LoadBehavior** doit avoir la valeur 0, 3 ou 16 (au format décimal) quand le complément VSTO est installé sur l'ordinateur de l'utilisateur final. Par défaut, Visual Studio affecte la valeur 3 à l'entrée **LoadBehavior** du complément VSTO quand vous le générez ou que vous le publiez.  
  
 Le tableau suivant répertorie toutes les valeurs possibles de l'entrée **LoadBehavior** . Certaines descriptions de ce tableau font référence au chargement manuel ou par programmation d'un complément VSTO. Pour charger un complément VSTO manuellement, cochez la case à côté du complément VSTO dans la boîte de dialogue **Compléments COM** de l'application. Pour charger un complément VSTO par programmation, affectez à la propriété <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> de l'objet <xref:Microsoft.Office.Core.COMAddIn> qui représente ce complément la valeur **true**.  
  
|Valeur (au format décimal)|État du complément VSTO|Comportement de chargement du complément VSTO|Description|  
|--------------------------|-------------------------|--------------------------------|-----------------|  
|0|Non chargé|Ne pas charger automatiquement|L'application ne tente jamais de charger le complément VSTO automatiquement. L'utilisateur peut essayer de charger manuellement le complément VSTO. Sinon, le complément VSTO peut être chargé par programmation.<br /><br /> Si le complément VSTO est correctement chargé, la valeur **LoadBehavior** reste 0, mais l'état du complément VSTO dans la boîte de dialogue **Compléments COM** est mis à jour pour indiquer que ce complément est chargé.|  
|1|Chargé|Ne pas charger automatiquement|L'application ne tente jamais de charger le complément VSTO automatiquement. L'utilisateur peut essayer de charger manuellement le complément VSTO. Sinon, le complément VSTO peut être chargé par programmation.<br /><br /> Bien que la boîte de dialogue **Compléments COM** indique que le complément VSTO est chargé au démarrage de l'application, ce complément n'est pas chargé tant qu'il n'est pas chargé manuellement ou par programmation.<br /><br /> Si l'application charge correctement le complément VSTO, la valeur de **LoadBehavior** passe à 0, et reste à 0 après la fermeture de l'application.|  
|2|Non chargé|Charger au démarrage|L'application ne tente pas de charger le complément VSTO automatiquement. L'utilisateur peut essayer de charger manuellement le complément VSTO. Sinon, le complément VSTO peut être chargé par programmation.<br /><br /> Si l'application charge correctement le complément VSTO, la valeur de **LoadBehavior** passe à 3, et reste à 3 après la fermeture de l'application.|  
|3|Chargé|Charger au démarrage|L'application tente de charger le complément VSTO au démarrage de l'application. Il s'agit de la valeur par défaut quand vous générez ou que vous publiez un complément VSTO dans Visual Studio.<br /><br /> Si l'application charge correctement le complément VSTO, la valeur de **LoadBehavior** reste égale à 3. Si une erreur se produit lors du chargement du complément VSTO, la valeur de **LoadBehavior** passe à 2, et reste à 2 après la fermeture de l'application.|  
|8|Non chargé|Charger à la demande|L'application ne tente pas de charger le complément VSTO automatiquement. L'utilisateur peut essayer de charger manuellement le complément VSTO. Sinon, le complément VSTO peut être chargé par programmation.<br /><br /> Si l'application charge correctement le complément VSTO, la valeur de **LoadBehavior** passe à 9.|  
|9|Chargé|Charger à la demande|Le complément VSTO est chargé seulement quand l'application le requiert, par exemple quand un utilisateur clique sur un élément d'interface utilisateur qui utilise des fonctionnalités du complément VSTO (par exemple un bouton personnalisé dans le ruban).<br /><br /> Si l'application charge correctement le complément VSTO, la valeur de **LoadBehavior** reste 9, mais l'état de ce complément dans la boîte de dialogue **Compléments COM** est mis à jour pour indiquer que le complément VSTO est actuellement chargé. Si une erreur se produit lors du chargement du complément VSTO, la valeur de **LoadBehavior** passe à 8.|  
|16|Chargé|Charger la première fois, puis charger à la demande|Définissez cette valeur si vous voulez que votre complément VSTO soit chargé à la demande. L'application charge le complément VSTO quand l'utilisateur exécute l'application pour la première fois. La prochaine fois que l'utilisateur exécute l'application, cette dernière charge tous les éléments d'interface utilisateur définis par le complément VSTO. Toutefois, le complément VSTO n'est pas chargé tant que l'utilisateur n'a pas cliqué sur un élément d'interface utilisateur associé à ce complément.<br /><br /> Quand l'application charge correctement le complément VSTO pour la première fois, la valeur de **LoadBehavior** reste 16 durant le chargement de ce complément. Après la fermeture de l'application, la valeur **LoadBehavior** passe à 9.|  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture des Solutions Office dans Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architecture des Compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Génération de Solutions Office](../vsto/building-office-solutions.md)   
 [Déploiement d’une solution Office](../vsto/deploying-an-office-solution.md)  
  
  