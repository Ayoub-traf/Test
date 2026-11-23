# Test

If(IsBlank(txtComm.Text);
    Notify("Un commentaire est obligatoire pour refuser"; NotificationType.Error);
    Patch('Modele PAC Trim'; LookUp('Modele PAC Trim'; ID = ThisItem.ID); {Decision: {Value: "Refusé"}; Commentaire: txtComm.Text; DecidePar: User().Email; DateDecision: Now()});;
    Patch(colPAC; ThisItem; {Decision: {Value: "Refusé"}; Commentaire: txtComm.Text; DecidePar: User().Email; DateDecision: Now()});;
    Notify("Échantillon refusé"; NotificationType.Warning)
)
