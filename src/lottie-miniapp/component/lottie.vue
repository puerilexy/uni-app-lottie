<template>
    <canvas canvas-id="lottie-canvas" class="lottie-canvas"></canvas>
</template>

<script>
import datajson from '@/lottie-miniapp/tool/data'
var _index = require('../lottie-miniapp.min.js');
var _index2 = _interopRequireDefault(_index);
function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { default: obj }; }
export default {
    props: {
        width: {
            type: Number,
            value: 100
        },
        height: {
            type: Number,
            value: 100
        },
        path: {
            type: String,
            observer: function observer() {
                this.init();
            }
        },
        animationData: {
            type: Object,
            observer: function observer() {
                this.init();
            }
        }
    },
    onReady () {
        this.init();
    },
    methods: {
        init: function init(animationData = datajson.data) {
            var width = arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : this.width;
            var height = arguments.length > 2 && arguments[2] !== undefined ? arguments[2] : this.height;
            var data = animationData || this.animationData;
            var dataPath = this.path;
            if (!data && !dataPath) return
            this.destory()
            var canvasContext = wx.createCanvasContext('lottie-canvas', this);
            canvasContext.canvas = {
                width: width,
                height: height
            }
            this.lottie = _index2.default.loadAnimation({
                renderer: 'canvas', // 只支持canvas
                loop: false,
                autoplay: true,
                animationData: data,
                path: dataPath,
                rendererSettings: {
                    context: canvasContext,
                    clearCanvas: true
                }
            })
        },
        destory: function destory() {
            if (this.lottie) {
                this.lottie.destroy();
                this.lottie = null;
            }
        }
    },
    onUnload () {
        this.destory();
    }
}
</script>

<style>
    .lottie-canvas {
        width: 100%;
        height: 100%;
    }
</style>