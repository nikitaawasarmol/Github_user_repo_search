<script>
export default {
  functional: true,
  props: {
    img: {
      type: String,
      default:
        "https://i.stack.imgur.com/frlIf.png"
    },
    circle: [Boolean, String],
    size: {
      type: String,
     
    }
  },
  render(h, context) {
    const { props } = context;
    return h(
      "img",
      {
        class: {
          circular: props.circle,
          sm: props.size === "sm",
        },
        attrs: {
          src: props.img,
          alt: "avatar"
        }
      },
      []
    );
  }
};
</script>
<style scoped>
.circular {
  border-radius: 50%;
  
}
.sm {
  width: 120px;
  height: 120px;
  float: left;
  padding: 0 10px;
}
</style>