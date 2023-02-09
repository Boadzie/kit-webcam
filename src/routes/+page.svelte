<script>

    let stream;
    let videoRef;

    async function getStream() {
        try {
            stream = await navigator.mediaDevices.getUserMedia({
                video: true,
                audio: false
            });
            videoRef.srcObject = stream;
        } catch (err) {
            console.error(err);
        }
        console.log(stream.getTracks()[0])
    }

    async function stopStream() {
        stream.getTracks().forEach(track => track.stop());
        videoRef.srcObject = null;
    }
</script>