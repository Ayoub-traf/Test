# Test

Patch('Modele PAC Trim'; LookUp('Modele PAC Trim'; ID = ThisItem.ID); {Decision: {Value: "Validé"}; Commentaire: txtComm.Text; DecidePar: User().Email; DateDecision: Now()});;
Patch(colPAC; ThisItem; {Decision: {Value: "Validé"}; Commentaire: txtComm.Text; DecidePar: User().Email; DateDecision: Now()});;
Notify("Échantillon validé"; NotificationType.Success)