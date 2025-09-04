(function(thisObj) {
    function moveToLayerCenterTime(layer) {
        if (layer) {
            var comp = layer.containingComp;
            if (comp) {
                // レイヤーの開始時間と終了時間を取得
                var inPoint = layer.inPoint;
                var outPoint = layer.outPoint;

                // センターの時間点を計算
                var centerTime = inPoint + (outPoint - inPoint) / 2;

                // タイムラインをセンターの時間に移動
                comp.time = centerTime;

                // 選択を解除
                layer.selected = false;
            }
        }
    }

    // 選択されたレイヤーを取得
    var selectedLayers = app.project.activeItem.selectedLayers;

    if (selectedLayers.length > 0) {
        // 最初の選択レイヤーのみを対象にする
        var targetLayer = selectedLayers[0];
        moveToLayerCenterTime(targetLayer);
    } else {
        alert("レイヤーを選択してください。");
    }

})(this);